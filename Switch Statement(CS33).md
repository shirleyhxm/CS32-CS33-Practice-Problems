
## CS33

### Decode Switch Statement from Assembly

*Contributed by Shirley He*.

Fill in the blanks of the C code. The assembly code and the memory status for the C code are given as follows. Assembly code:  

    08048430 <foo>:
        8048430:   push   %ebp                  8048454:   mov   %ecx,%eax
        8048431:   mov    %esp,%ebp             8048456:   or    %edx,%eax
        8048433:   push   %ebx                  8048458:   jmp   804846f <foo+0x3f>
        8048434:   mov    0x8(%ebp),%ebx        804845a:   mov   %esi,%esi
        8048437:   xor    %eax,%eax             804845c:   mov   %ecx,%eax
        8048439:   cmp    $0x4,%ebx             804845e:   xor   %edx,%eax
        804843c:   mov    0xc(%ebp),%ecx        8048460:   jmp   804846f <foo+0x3f>
        804843f:   mov    0x10(%ebp),%edx       8048462:   mov   %esi,%esi
        8048442:   ja     804846f <foo+0x3f>    8048464:   mov   %ecx,%eax
        8048444:   jmp    *0x8048500(,%ebx,4)   8048466:   not   %eax
        804844b:   nop                          8048468:   jmp   804846f <foo+0x3f>
        804844c:   mov    %ecx,%eax             804846a:   mov   %esi,%esi
        804844e:   and    %edx,%eax             804846c:   lea   (%edx,%ecx,1),%eax
        8048450:   jmp    804846f <foo+0x3f>    804846f:   mov   (%esp,1),%ebx
        8048452:   mov    %esi,%esi             8048472:   leave
                                                8048473:   ret

Memory information given by gdb: 

    >gdb foo
    (gdb) x /8w 0x8048500
    0x8048500 : 0x0804844c 0x08048454 0x0804845c 0x08048464  
    0x8048510 : 0x0804846c 0x00000000 0x00000000 0x00000000`

C code:

    int foo(int op, int a, int b)
    {
        int result = 0;
        switch (op)
        {
            case 0: ______________ ;
            case 1: ______________ ;
            case 2: ______________ ;
            case 3: ______________ ;
            case 4: ______________ ;
        }
        return result;
    }

#### Solution

    int foo (int op, int a, int b)
    {
        int result = 0;
        switch (op)
        {
            case 0: result = a & b; break;
            case 1: result = a | b; break;
            case 2: result = a ^ b; break;
            case 3: result = ~a   ; break;
            case 4: result = a + b; break;
        }
        return result;
    }