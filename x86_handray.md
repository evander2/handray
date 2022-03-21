# x86_handray

main 함수를 handray 하였다.


```C
int main(void){
    char buf[40];
    int a=0x04030201;
    
    fgets(buf, 0x2d, stdin);
    printf("\n[buf]: %s\n", buf);
    printf("[check] %p\n",local_14);
    
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

먼저 
