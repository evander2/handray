# asm.c 의 main 함수 어셈블리 코드

```
push   %rbp
mov    %rsp,%rbp
sub    $0x10,%rsp
movl   $0x2022,-0x4(%rbp)
movl   $0x314,-0x8(%rbp)
mov    -0x8(%rbp),%edx
mov    -0x4(%rbp),%eax
mov    %edx,%esi
mov    %eax,%edi
call   0x1129 <add>
mov    %eax,-0xc(%rbp)
mov    -0x8(%rbp),%edx
mov    -0x4(%rbp),%eax
mov    %edx,%esi
mov    %eax,%edi
call   0x113d <sub>
mov    %eax,-0x10(%rbp)
mov    -0xc(%rbp),%eax
imul   -0x10(%rbp),%eax
leave
ret
```

asm.c의 어셈블리어 코드를 작성하였다.
먼저 rsp, rbp를 설정하여 함수의 시작 부분을 작성한다. 
이후 rsp를 감소시켜 공간을 할당하고, rbp를 기준으로 연산을 하여 주어진 값을 할당한다. 그리고 그 값들을 edx와 eax에 옮긴다.
그 뒤 값들을 edi와 esi에 옮긴 후 add 함수를 호출한다. add 함수에서는 eax에 덧셈을 한다.
이후 -0xc(%rbp)에 add연산의 결과를 저장하고 같은 방식으로 연산을 한 뒤 sub함수를 호출한다.
sub함수의 결과를 -0x10(%rbp)에 저장한 뒤 add연산의 결과를 eax로 옮긴다.
그 뒤 imul 명령어를 이용해 sub함수의 결과와 add함수의 결과를 곱해 eax에 저장한다.
