---
layout: post
title: An one-line (and fast) macro to determine endianness at runtime
categories: programming_technique
---

See the code below. Explanation in the comments.

```c
#include <stdio.h>
#include <stdint.h>
 
/* Okay. Explain a bit about how this works.
 * "\0\xff": a string litteral with 2 chars. The first char is '\0' - the NULL
 * character. It has a numerical value of 0 (ASCII). The second char is written
 * in the form of hexadecimal-escape-sequence '\xff', which has the numerical
 * value of the hexadecimal integer, in this case is 0xFF. See ISO C99, section
 * 6.4.4.4 & 6.4.5.
 * The net result of this string litteral definition is 2 bytes written in to
 * memory with layout like this:
 * Addr:   Byte 1  Byte 2
 *       +-----------------+
 *       |00000000|11111111|
 *       +-----------------+
 *          00       FF
 * Casting this 2 bytes into a uint16_t value results to different values on Big
 * and Little endian machines
 * +  On a big endian machine, the value is interpreted as 0x00FF < 0x0100
 * +  On a little endian machine, the value is interpreted as 0xFF00 > 0x0100
 */
#define IS_BIG_ENDIAN (*(uint16_t *)"\0\xff" < 0x0100)
 
int main(void)
{
    if (IS_BIG_ENDIAN)
        printf("This computer is Big Endian\n");
    else
        printf("This computer is Little Endian\n");
    return 0;
}
```

