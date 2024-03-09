## rev/cyber kingdom
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/539135d2-3729-4f28-b121-a987dd29df97)
### by disassembling in ghidra
```

undefined8 main(void)

{
  uint uVar1;
  long in_FS_OFFSET;
  int local_16c;
  int local_168;
  int local_164;
  int local_160;
  uint auStack_158 [36];
  int local_c8 [36];
  byte local_38 [40];
  long local_10;
  
  local_10 = *(long *)(in_FS_OFFSET + 0x28);
  srand(0x7b);
  for (local_16c = 0; local_16c < 0x23; local_16c = local_16c + 1) {
    uVar1 = rand();
    auStack_158[local_16c] = uVar1 & 0xf;
  }
  puts("\n\t||| Welcome to my Cyber Kingdom |||");
  puts("||| I have a quick task for you if you don\'t mind |||");
  puts("|| Find the correct flag for me and prove yourself! ||\n");
  printf("Please enter the flag: ");
  fgets((char *)local_38,0x24,stdin);
  for (local_168 = 0; local_168 < 0x23; local_168 = local_168 + 1) {
    local_38[local_168] = local_38[local_168] ^ (byte)auStack_158[local_168];
  }
  local_c8[0] = 0x72;
  local_c8[1] = 0x6d;
  local_c8[2] = 0x60;
  local_c8[3] = 0x65;
  local_c8[4] = 0x73;
  local_c8[5] = 0x62;
  local_c8[6] = 0x68;
  local_c8[7] = 0x7a;
  local_c8[8] = 0x6c;
  local_c8[9] = 0x7a;
  local_c8[10] = 0x77;
  local_c8[11] = 100;
  local_c8[12] = 0x31;
  local_c8[13] = 0x54;
  local_c8[14] = 0x77;
  local_c8[15] = 0x31;
  local_c8[16] = 0x6c;
  local_c8[17] = 99;
  local_c8[18] = 0x59;
  local_c8[19] = 0x67;
  local_c8[20] = 0x62;
  local_c8[21] = 0x31;
  local_c8[22] = 0x6c;
  local_c8[23] = 0x58;
  local_c8[24] = 0x31;
  local_c8[25] = 0x7d;
  local_c8[26] = 0x53;
  local_c8[27] = 0x7e;
  local_c8[28] = 0x3b;
  local_c8[29] = 0x62;
  local_c8[30] = 0x69;
  local_c8[31] = 0x30;
  local_c8[32] = 0x6c;
  local_c8[33] = 0x31;
  local_c8[34] = 0x72;
  local_164 = 0;
  for (local_160 = 0; local_160 < 0x23; local_160 = local_160 + 1) {
    if (local_c8[local_160] == (int)(char)local_38[local_160]) {
      local_164 = local_164 + 1;
    }
  }
  if (local_164 == 0x23) {
    puts("\nYou got it!!");
  }
  else {
    puts("\nNope, that\'s not the right path");
  }
  if (local_10 != *(long *)(in_FS_OFFSET + 0x28)) {
                    /* WARNING: Subroutine does not return */
    __stack_chk_fail();
  }
  return 0;
}

```
- flag length is 35
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/da9cc6c9-48fb-45bd-8d4d-492739d65f7a)
- so here there is random number generation but it uses a seed so same random numbers will come all the time
- so austack contains the random number
- our user input is in local38
- it is xored with the austack
- the result is compared with the localc8
- our_input^the_fixed_array=localc8
- so to get the our_input which must be the flag
- our_input=the_fixed_array^localc8
- the fixed array can be found by
```
#include <stdio.h>
#include <stdlib.h>

int main() {
    srand(0x7b);
    int aray[35]={0};

    for (int i = 0; i < 35; i++) { 
        int x=rand() & 0xf;
        printf("%d,", x); 
    }

    printf("done");
    return 0;
}

```
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/00b633d2-45bb-4376-a45a-b09baf610097)
### solve.py
```
length=35
random_numbers=[1,5,1,14,7,11,11,14,10,1,0,12,1,11,4,5,5,7,6,1,14,5,11,7,0,14,12,12,15,12,13,0,1,14,15]
local_c8=['']*35
local_c8[0] = 0x72 
local_c8[1] = 0x6d 
local_c8[2] = 0x60 
local_c8[3] = 0x65 
local_c8[4] = 0x73 
local_c8[5] = 0x62 
local_c8[6] = 0x68 
local_c8[7] = 0x7a 
local_c8[8] = 0x6c 
local_c8[9] = 0x7a 
local_c8[10] = 0x77 
local_c8[11] = 100 
local_c8[12] = 0x31 
local_c8[13] = 0x54 
local_c8[14] = 0x77 
local_c8[15] = 0x31 
local_c8[16] = 0x6c 
local_c8[17] = 99 
local_c8[18] = 0x59 
local_c8[19] = 0x67 
local_c8[20] = 0x62 
local_c8[21] = 0x31 
local_c8[22] = 0x6c 
local_c8[23] = 0x58 
local_c8[24] = 0x31 
local_c8[25] = 0x7d 
local_c8[26] = 0x53 
local_c8[27] = 0x7e 
local_c8[28] = 0x3b 
local_c8[29] = 0x62 
local_c8[30] = 0x69 
local_c8[31] = 0x30 
local_c8[32] = 0x6c 
local_c8[33] = 0x31 
local_c8[34] = 0x72 
# print(local_c8)
for i in range(len(local_c8)):
    print(chr((local_c8[i])^random_numbers[i]),end='')
```
it is just doing the xor between c8 and the fixed random numbers
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/94b32bb4-47e5-468c-8e0d-39c8e5b48d3a)
shaktictf{wh0_s4id_fl4g_1s_r4nd0m?} 

