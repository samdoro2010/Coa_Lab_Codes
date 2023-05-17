ATA SEGMENT
    A DB 5,9,2,7,2,1
    COUNT EQU 6
DATA ENDS
CODE SEGMENT
    ASSUME CS:CODE, DS:DATA
START:      MOV AX,DATA
            MOV DS,AX
            MOV CX,COUNT
            MOV DX,CX
            DEC DX
            MOV SI,0
OUT_LOOP:   CMP DX,SI
            JZ NXT
            MOV AL,A[SI]
            MOV BL,A[SI+1]
            CMP AL,BL
            JA SWAP
            INC SI
            JMP OUT_LOOP
SWAP:       MOV A[SI],BL
            MOV A[SI+1],AL
            INC SI
            JMP OUT_LOOP
NXT:        MOV SI,0H
            SUB CX,1
            CMP CX,0                
            JNZ OUT_LOOP  
            MOV CX,COUNT
            MOV SI,0
PRI:        MOV DL,A[SI]
            ADD DL,48
            MOV AH,2H
            INT 21H
            INC SI
            LOOP PRI
CODE ENDS
END START
