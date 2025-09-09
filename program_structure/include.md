## директива include
Вставляет код из одного файла в другой. Принимает имя файла (из той же папки)

Сделаем файл sum.asm c процедурой sum
```
sum proc
    mov rax, rcx
    add rax, rdx
    ret
sum endp
```

Подключим sum.asm в главный файл программы - main.asm
```
.code
include sum.asm

main proc
    mov rcx, 6
    mov rdx, 2
    call sum
    ret
main endp
end
```
Вуаля!

### headerguards
Если сделать больше одного include того же файла, будет дублирование, путаница и ошибка компиляции. 

Нужны header guards. Изменим файл main.asm:
```
.code 
ifndef sum_asm
    sum_asm = 0
    include sum.asm
endif

main proc
    mov rcx, 6
    mov rdx, 3
    call sum
    ret
main endp
end
```

Оператор условной компиляции ifndef в качестве операнда принимает переменную.

