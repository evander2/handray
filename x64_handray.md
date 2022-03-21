# x64_handray


```C
int main(void){
    int iVar1;
    long i;
    long *plVar3;
    long in_FS_OFFSET;
    long ssp;
    byte bVar4;
    long local_80;
    long local_78;
    long local_70;
    long local_68 [11];

    bVar4 = 0;
    ssp = *(long *)(in_FS_OFFSET + 0x28);
    setup();
    while( true ) {
        local_80 = 0;
        local_78 = 0;
        local_70 = 0;
        plVar3 = local_68;
        for (i = 10; i != 0; i = i + -1) {
            *plVar3 = 0;
            plVar3 = plVar3 + (ulong)bVar4 * -2 + 1;
        }
        printf("Input: ");
        iVar1 = __isoc99_scanf("%ld %ld %ld",&local_80,&local_78,&local_70);
        if (iVar1 != 3) break;
        local_68[local_70] = local_78 + local_80;
        printf("Result: %ld",local_68[local_70]);
    }
    if (ssp != *(long *)(in_FS_OFFSET + 0x28)) __stack_chk_fail();
    
    return 0;
}
```

먼저 스택에 0x80만큼의 공간을 할당하고, FS_OFFSET으로부터 ssp(Stack Smashing Protector)를 설정하여 스택이 파괴되지 않았는지 감지한다. main 함수가 끝날 때 ssp를 검사하여 ssp가 변경되었다면 __stack_chk_fail() 함수를 호출한다.  
안녕 ㅇㅇㅇㅇ


rep stos 명령어는 뒤에 오는 명령을 ecx에 저장된 횟수만큼 반복하는 것이므로 ecx에 저장된 값을 감소시키면서 10회 반복한다.





