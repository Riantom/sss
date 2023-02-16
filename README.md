# sss
fibonacci:
MOV SI, 500 ; Load 500 into the source index register
MOV DI, 600
; Load 600 into the destination index register
MOV AX, 0000 ; Clear AX register
MOV CL, [SI]
Load the block size (value of n)
MOV BL, CL ;Also store n into BL
INC SI ;Point to next location
L1: ADD AL, [SI] ; Add AL and memory element pointed by SI
ADC AH, 00 ;Add AH + 00 and Carry
INC SI ;Point to next location
DEC CL ;Decrease CL register by 1
JNZ L1 ;If Z = 0, jump to L1
DIV BL ;Otherwise divide it with BL
MOV [DI], AX ;Store the result of division into memory HLT Terminate the program

average:
MOV SI, 500H ; Load 500 into the source index register
MOV DI, 600H
; Load 600 into the destination index register
MOV AX, 0000 ; Clear AX register
MOV CL, [SI] ;Load the block size (value of n)
MOV BL, CL ;Also store n into BL
INC SI ;Point to next location
L1: ADD AL, [SI] ; Add AL and memory element pointed by SI
ADC AH, 00 ;Add AH + 00 and Carry
INC SI ;Point to next location
DEC CL ;Decrease CL register by 1
JNZ L1 ;If Z = 0, jump to L1
DIV BL ;Otherwise divide it with BL
MOV [DI], AX ;Store the result of division into memory
HLT ;Terminate the program

MIN:
MOV SI, 500H
MOV DI, 600H
MOV CL, [SI]
MOV CH, 00
INC SI
MOV AL, [SI]
DEC CX
L2:INC SI
MOV BL, [SI]
CMP AL, BL ;subtract the value of BL register from AL and it modify flag registers
JC L1 ;jump to 0417 address if carry flag is set
MOV AL, BL ;moves the content of BL register to AL register
L1:LOOP L2 ;runs loop till CX not equal to Zero and decrease the value of CX by 1
MOV [DI], AL ;moves the content of AL to [DI]
HLT

MAX:
MOV SI, 500H
MOV DI, 600H
MOV CL, [SI]
MOV CH, 00
INC SI
MOV AL, [SI]
DEC CX
L2:INC SI
MOV BL, [SI]
CMP AL, BL ;subtract the value of BL register from AL and it modify flag registers
JNC L1 ;jump to 0417 address if carry flag is set
MOV AL, BL ;moves the content of BL register to AL register
L1:LOOP L2 ;runs loop till CX not equal to Zero and decrease the value of CX by 1
MOV [DI], AL ;moves the content of AL to [DI]
HLT

FACTORIAL:
MOV SI, 500H
MOV DI, 600H
MOV CX, [SI]  
MOV AX,0001H
MOV DX,0000H
L1:MUL CX
LOOP  L1
MOV [DI], AX
MOV [DI+2],DX ;moves the content of AL to [DI]
HLT

SUM OF DIGITS:
MOV AL, [2000H] ;Take the number from memory
MOV AH, AL ; Load AH with AL
MOV CL, 04H ;Set counter at 0004
AND AL, 0FH ;Mask upper nibble of AL
ROL AH, CL ;Rotate 4 times
AND AH, 0FH ; Mask upper nibble of AH
ADD AL, AH ; Add AL and A L registers
MOV [2001H], AL;Store sum at memory 2001
HLT ;Terminate the program

PRIME:
MOV CL,00H     ; /*Clearing the registers*/
MOV DX,0000H      ;/*Clearing the registers*/
MOV AX,[500H]  ;/*Assume the number is store in memory 1500*/
MOV BX,AX      ;/*Copy the value in AX to BX */
L1:DEC BX
DIV BX         ;/*Dividing*/
CMP DX,0000    ;/*Check for Reminder, Reminder is stored in DX*/
JZ L2
MOV DX,0000H
MOV AX,[500H]      ;/*Clearing DX*/
CMP BX,0002H
JNZ L1
MOV CL,01H
L2:MOV [502H],CL  ;/*Storing the result*/
HLT
