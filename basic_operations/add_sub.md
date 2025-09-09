## add sub inc dec
### add
сложение двух операндов
```
add destination, source

; destination += source
```
При этом константы и непосредственные операнды размером не более 32 бит.

```
.code
main proc
    mov rdx, 6
    mov rax, 10
    add rax, rdx ; rax += rdx
    ; в итоге будет 16
    ret
main endp
end
```

### sub 
вычитание - аналогично
```
.code
main proc
    mov rdx, 6
    mov rax, 10
    sub rax, rdx 
    ret
main endp
end
```
### inc и dec
инкремент и декремент для регистров и переменных
```
.code
main proc
    mov rdx, 3
    mov rax, 8
    inc rdx
    dec rax
    ret
main endp
end
```