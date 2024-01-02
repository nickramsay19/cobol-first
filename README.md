## Data
* VALUE
    `01 WS-A PIC 9(4) VALUE 1234`
* RENAMES - simply renames the variable to another, or to a grouping (concatenation) of many other data
    ```
    01 WS-A PIC 9(1).
    01 WS-R RENAMES WS-A.
    ```
    ```
    01 WS-A PIC 9(1).
    01 WS-B PIC 9(1).
    01 WS-R RENAMES WS-A, WS-B.
    ```
    ```
    01 WS-A PIC 9(1).
    01 WS-B PIC 9(1).
    01 WS-C PIC 9(1).
    01 WS-R RENAMES WS-A THROUGH WS-C.
    ```
* REDEFINES - like RENAMES, but can allow access to only some of the data, and optionally, as a different different type
    ```
    01 WS-A PIC 9(4).
    01 WS-B REDEFINES WS-A PIC A(3).
    ```
* USAGE - tells the OS how to store the data
    * `01 WS-A PIC 9(7)A(1) USAGE IS DISPLAY` => store as a single byte

## Verbs
* ACCEPT
* DISPLAY
* INITIALIZE - necessary for initializing group items or elementary items (when VALUE cannot be used in their declaration)
    * `INITIALIZE A, B.` => Initializes A and B
    * cannot be used for data with a `RENAME` clause
* MOVE
    * `MOVE 25 TO B.`
    * `MOVE A TO B.`
* ADD
    * `ADD A B TO C.` => `C += A + B`
    * `ADD A B TO C D.` => `C += A + B; D += A + B`
    * `ADD A TO B GIVING C.` => `C = A + B`
    * `ADD A B TO C GIVING D.` => `D = A + B + C`
* SUBTRACT
* MULTIPLY
* DIVIDE
    * `DIVIDE A INTO B.` => `B /= A`
    * `DIVIDE A BY B GIVING C REMAINDER D.` => `C = A/B; D = A%B`
* COMPUTE - a replacement for ADD, SUBTRACT, etc
    * `COMPUTE C= (X * Y) - (A / B) + Z.`
