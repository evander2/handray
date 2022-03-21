# x86_handray

main 함수를 handray 하였다.


```C
int main(void){
    int a=0x04030201;
    char buf[40];
    
    fgets(buf, 0x2d, stdin);
    printf("\n[buf]: %s\n", buf);
    printf("[check] %p\n", a);
    
    if((a != 0x04030201) && (a != L'\xdeadbeef')){
        puts("\nYou are on the right way!");
    }
    if(a == L'\xdeadbeef'){
        puts("Yeah dude! You win!\nOpening your shell...");
        system("/bin/dash");
        puts("Shell closed! Bye.");
    }
    return 0;
}


```

먼저 [ebp-0xc]에 0x04030201을 저장하고, [ebp-0x34]에 char 배열을 저장하므로 int a=0x04030201과 char buf[40]을 선언한다.  
그리고 stdi, 0x2d, buf를 인자로 주고 fgets 함수를 호출한다. 이후 buf와 "\n[buf]: %s\n"를 인자로 주고 printf 함수를 호출하고, a와 "[check] %p\n"을 인자로 주고 printf 함수를 호출한다.  
그리고 a와 0x04030201이 다르고 a와 L'\xdeadbeef'가 다르면 그대로 진행해 puts("\nYou are on the right way!")를 출력한다. 그렇지 않으면 jmp해 a가 L'\xdeadbeef'인지 다시 비교하고 그렇다면 puts("Yeah dude! You win!\nOpening your shell..."), system("/bin/dash"), puts("Shell closed! Bye.")를 연달아 실행한다.  
그렇지 않다면 jmp하고 함수 에필로그를 실행한다.
