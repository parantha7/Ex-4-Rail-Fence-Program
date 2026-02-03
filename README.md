# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
int main() {
    char str[1000];
    int rails, len;
    int i, j;

    printf("Enter a Secret Message:\n");
    fgets(str, sizeof(str), stdin);
    str[strcspn(str, "\n")] = '\0';

    printf("Enter number of rails:\n");
    scanf("%d", &rails);

    len = strlen(str);
    char rail[rails][len];
    for (i = 0; i < rails; i++) {
        for (j = 0; j < len; j++) {
            rail[i][j] = '\n';
        }
    }
    int row = 0;
    int dir_down = 0; 

    for (j = 0; j < len; j++) {
        rail[row][j] = str[j];
        if (row == 0)
            dir_down = 1;
        else if (row == rails - 1)
            dir_down = 0;
        row += dir_down ? 1 : -1;
    }
    printf("Encrypted Message: ");
    for (i = 0; i < rails; i++) {
        for (j = 0; j < len; j++) {
            if (rail[i][j] != '\n')
                printf("%c", rail[i][j]);
        }
    }
    printf("\n");

    return 0;
}
```

# OUTPUT
<img width="498" height="382" alt="image" src="https://github.com/user-attachments/assets/45177622-26b8-4eee-917a-66ba59be185a" />


# RESULT
Thus the implementation of Rail Fence had been executed successfully.
