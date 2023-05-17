LARGEST NUMBER
DATA SEGMENT
    array db 0,1 
ENDS

CODE SEGMENT 
    ASSUME DS:DATA CS:CODE
START:
    MOV AX,DATA
    MOV DS,AX
    MOV AL,array[si]
    MOV SI,0
    MOV BL,1
    
    LOOP1:INC SI
          CMP AL,array[SI]
          JGE LOOP2
          MOV AL,array[SI] 
          
    LOOP2:DEC BL
          JNZ LOOP1 
           
    ADD AL,30H       
    MOV DL,AL
    MOV AH,02h
    INT 21h
    hlt   

ENDS
END START
