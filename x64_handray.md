# x64_handray


```C
int main(void){
    int v, i;
    long *ptr;
    long in_FS_OFFSET;
    long ssp;
    long local_68, local_70, local_78;
    long local_60[11];

    ssp = *(long *)(in_FS_OFFSET + 0x28);
    setup();
    while( true ) {
        local_78 = 0;
        local_70 = 0;
        local_68 = 0;
        ptr = local_60;
        for (i = 10; i != 0; i = i + -1) {
            *ptr = 0;
            ptr = ptr + 1;
        }
        printf("Input: ");
        v = __isoc99_scanf("%ld %ld %ld",&local_78,&local_70,&local_68);
        if (v != 3) break;
        local_60[local_68] = local_70 + local_78;
        printf("Result: %ld",local_60[local_68]);
    }
    if (ssp != *(long *)(in_FS_OFFSET + 0x28)) __stack_chk_fail();
    
    return 0;
}
```

먼저 스택에 0x80만큼의 공간을 할당하고, FS_OFFSET으로부터 ssp(Stack Smashing Protector)를 설정하여 스택이 파괴되지 않았는지 감지한다. main 함수가 끝날 때 ssp를 검사하여 ssp가 변경되었다면 __stack_chk_fail() 함수를 호출한다.  
그 뒤에는 setup() 함수를 호출한다. 어셈블리어 구문에서 main+28로 jmp하는 부분이 있으므로 while(true) 구문으로 계속 반복한다. 반복문 내부에서는 선언한 local_78, local_70, local_68 변수를 0으로 초기화한 뒤 포인터 변수를 local_60을 가리키도록 한다. 이후 포인터 ptr이 가리키는 지점(\*ptr)을 0으로 초기화하고 ptr을 1씩 증가시키는 구문을 실행한다. rep stos 명령어는 eax값을 edi에 담긴 주소 안에 저장하는 연산을 ecx에 저장된 횟수만큼 반복하는 것이므로 a번 반복한다. 변수 i를 10부터 1까지 줄이며 연산을 실행한다.  
이후 "Input: "을 출력한다. 그리고 local_68, local_70, local_78을 __isoc99_scanf 함수를 통해 입력받는다. v값은 포맷 형식에 알맞은 값이 들어온 개수이므로 3이 아니면 반복문 실행을 종료한다.  
그 뒤 local_60의 local_68 위치의 값에 local_70과 local_78을 더한 값을 저장한다. local_68은 숫자이고 x64 환경이므로 8을 곱해서 더하여 주소에 접근하고 있다. "Result: %ld"와 더해 저장한 결과를 printf에 인자로 전달해 출력한다.  
이후 함수 에필로그로 main 함수를 마무리한다.



