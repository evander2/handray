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
그리고 
