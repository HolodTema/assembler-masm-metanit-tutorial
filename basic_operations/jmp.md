## jmp
assembler может в одной точке программы перейти к другой части программы (в других языках это ключевое слово goto). 

Такие переходы бывают условными и безусловными. 

### jmp - безусловный переход
jmp имеет следующие формы:
```
jmp metka_name
jmp register
jmp variable
```
### jmp на метку
```
.code
main proc
    mov rdx, 11
    jmp mymetka
    mov rdx, 22 ; не выполнится
mymetka:
    mov rax, rdx
    ret
main endp
end
```
В итоге rdx будет равным 11

### jmp на регистр
Можно сделать jmp на 64-битный регистр, который хранит адрес какой-то инструкции.

Например. поместим метку в регистр и прыгнем на регистр:
```
.code
main proc
    mov rbx, return
    mov rax, 22
    jmp rbx
    mov rax, 33 ; не выполнится
return: 
    ret
main endp
end
```

### jmp на переменную
можно прыгнуть на адрес в переменной. Такая переменная должна быть qword (4-слово 64 бита размером).

Ибо 8 байт = 64 бит = qword - это размер адреса в архитектуре x64

```
.code
main proc
    mov rax, 23
    jmp qwRet
    mov rax, 33 ; не выполнится
return: 
    ret
qwRet qword return ; создали переменную
main endp
end
```
Причем здесь переменную создали в процедуре main после остального кода (да, так можно)