LCM
a db 2
b db 3

mov al,a
mov bl,b
mov ah,0
mov bh,al
div bl
cmp ah,0
jz exit
loop loop1
loop1:
mov ah,0
mov al,bh 
add al,a
mov bh,al
div bl
cmp ah,0
jz exit
loop loop1
exit:
mov dl,bh
add dl,48
mov ah,2
int 21h