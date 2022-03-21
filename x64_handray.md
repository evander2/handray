# x64_handray


```C
int main(void){
  int iVar1;
  long lVar2;
  long *plVar3;
  long in_FS_OFFSET;
  byte bVar4;
  long local_80;
  long local_78;
  long local_70;
  long local_68 [11];
  long local_10;
  
  bVar4 = 0;
  local_10 = *(long *)(in_FS_OFFSET + 0x28);
  setup();
  while( true ) {
    local_80 = 0;
    local_78 = 0;
    local_70 = 0;
    plVar3 = local_68;
    for (lVar2 = 10; lVar2 != 0; lVar2 = lVar2 + -1) {
      *plVar3 = 0;
      plVar3 = plVar3 + (ulong)bVar4 * -2 + 1;
    }
    printf("Input: ");
    iVar1 = __isoc99_scanf("%ld %ld %ld",&local_80,&local_78,&local_70);
    if (iVar1 != 3) break;
    local_68[local_70] = local_78 + local_80;
    printf("Result: %ld",local_68[local_70]);
  }
  if (local_10 != *(long *)(in_FS_OFFSET + 0x28)) {
                    /* WARNING: Subroutine does not return */
    __stack_chk_fail();
  }
  return 0;
}
```

먼저 




