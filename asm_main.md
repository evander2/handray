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
eave 
```

먼저 rsp, rbp를 설정하여 함수의 시작 부분을 작성한다. 
이후 rsp를 감소시켜 공간을 할당하고, rbp를 기준으로 연산을 하여 주어진 값을 할당한다. 그리고 그 값들을 edx와 eax에 옮긴다.
