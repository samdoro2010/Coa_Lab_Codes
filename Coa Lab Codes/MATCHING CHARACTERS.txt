MATCHING CHARACTERS
DATA SEGMENT 100h   
    msg db 'SRM AP'    
    count equ ($ - msg)  
    pass db ' '   
DATA ENDS            
CODE SEGMENT         
ASSUME DS:DATA,CS:CODE
START:           
    mov ax,data  
    mov ds,ax 
    lea si,msg   
    lea di,pass 
    mov cx,count
    loop1: 
        mov  al,[si]
        cmp al,[di]
        je l2  
        inc si     
        loop loop1
    l1:
        mov dl,'N'
        mov ah,2h
        int 21h
        hlt  
    l2:
        mov dl,'Y'
        mov ah,2h
        int 21h
        hlt   
    CODE ENDS        
END START
