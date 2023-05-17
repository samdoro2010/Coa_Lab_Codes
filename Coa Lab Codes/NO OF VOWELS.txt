NO OF VOWELS
DATA SEGMENT 100h
    v db 'AEIOUaeiou' 
    count equ ($ - v)
    msg db 'aeiou' 
    len equ ($ - msg) 
    print DB 'Number of Vowels : $'
    DATA ENDS     

CODE SEGMENT
    ASSUME DS:DATA,CS:CODE
    START:
    MOV AX,DATA
    MOV DS,AX
    MOV BL,0
    MOV BH,0
    LEA DI,MSG
    LEA DX,PRINT
    MOV AH,9H
    INT 21H
    L1:
    LEA SI,V
    MOV CX,COUNT 
    
    LOOP1: 
    MOV AL,[SI] 
    CMP AL,[DI]
    JE L2
    L:
    INC SI
    LOOP LOOP1 
    INC BH
    CMP BH,LEN
    JE COMPLETED
    INC DI
    JMP L1
    
    L2:
    INC BL
    JMP L
                
   COMPLETED:
      MOV DL,BL
      add dl,48
      MOV AH,2H
      INT 21H  
      
   CODE ENDS
END START