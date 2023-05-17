GCD
mov al,2
mov bl,5
mov ah,0   
cmp al,bl
ja next  
xchg al,bl
next:
mov bh,bl
div bl
cmp ah,0
je l1    
mov al,bh
mov bl,ah  
mov ah,0
jmp next
l1: 
mov dl,bl
add dl,48
mov ah,2h
int 21h
