## rev/waruprev
```
  local_58 = 0x316e64333364217d;---1nd33d!}
  local_50 = 0x346c6c336e67335f;----4ll3ng3_
  local_48 = 0x34726d55705f6368;---4rmUp_ch
  local_40 = 0x31355f345f77;-----15_4_w
  uStack_3a = 0x735f;--------s_
  uStack_38 = 0x74667b746831;---tf{th1
  local_32 = 0x7368616b746963;---shaktic
  shaktictf{th1s_15_4_w4rmUp_ch4ll3ng3_1nd33d!}
```
https://www.rapidtables.com/convert/number/hex-to-ascii.html
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/109a92ae-27c1-4bb5-a1d6-6956bcf51756)
```

undefined8 main(undefined8 param_1,undefined8 param_2)

{
  int iVar1;
  size_t sVar2;
  long in_FS_OFFSET;
  char acStack_e8 [104];
  undefined8 uStack_80;
  undefined4 local_6c;
  undefined8 local_68;
  char *local_60;
  undefined8 local_58;
  undefined8 local_50;
  undefined8 local_48;
  undefined6 local_40;
  undefined2 uStack_3a;
  undefined6 uStack_38;
  undefined8 local_32;
  long local_20;
  
  local_20 = *(long *)(in_FS_OFFSET + 0x28);
  local_6c = 100;
  local_68 = 99;
  local_60 = acStack_e8;
  printf("Enter the flag: ",param_2,3);
  fgets(local_60,100,stdin);
  sVar2 = strcspn(local_60,"\n");
  local_60[sVar2] = '\0';
  reverseString(local_60);
  local_58 = 0x316e64333364217d;
  local_50 = 0x346c6c336e67335f;
  local_48 = 0x34726d55705f6368;
  local_40 = 0x31355f345f77;
  uStack_3a = 0x735f;
  uStack_38 = 0x74667b746831;
  local_32 = 0x7368616b746963;
  iVar1 = strcmp(local_60,(char *)&local_58);
  if (iVar1 == 0) {
    puts("\nYou got it!!");
  }
  else {
    puts("Oops, that\'s not the correct flag");
  }
  if (local_20 != *(long *)(in_FS_OFFSET + 0x28)) {
                    /* WARNING: Subroutine does not return */
    uStack_80 = 0x10137e;
    __stack_chk_fail();
  }
  return 0;
}


```
## blankshell/pwn ---not comleted
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/8a8ef687-ac36-4627-b9ac-ce211d156cfe)
- we see agent 007
- in linux file permissions
- https://kb.iu.edu/d/abdb
- that means we have read write execute permissions
- we try to execute /bin/ls .
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/41a72019-d7aa-43d5-a3c9-445c36b24e99)
- we get illegal hardware instruciton
  
