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
## operation ultra/rev
### given ultra.py
```
import base64

def func_1(unk_str0, unk_str):
    flag_len = len(unk_str0)
    unk_str_len = len(unk_str)

    unk_str1 = bytearray(unk_str0, 'utf-8')

    for i in range(flag_len):
        unk_str1[i] = unk_str1[i] ^ ord(unk_str[i % unk_str_len])

    return unk_str1.decode('utf-8')

def func_2(unk_str0):
    flag_len = len(unk_str0)
    unk_str3 = [''] * flag_len

    j = 0

    for i in range(0, flag_len , 4):
        unk_str3[j] = unk_str0[i]
        unk_str3[j + 1] = unk_str0[i + 1]
        j += 2

    for i in range(2, flag_len, 4):
        unk_str3[j] = unk_str0[i]
        unk_str3[j + 1] = unk_str0[i + 1]
        j += 2

    return ''.join(unk_str3)

def main():
    unk_str = "U2hhZG93MjAyNA=="
    unk_str = base64.b64decode(unk_str.encode('ascii')).decode('ascii')

    unk_str0 = input("Enter the input: ")

    unk_str1 = func_1(unk_str0, unk_str)

    unk_str2 = func_2(unk_str1)

    unk_arr0 = [32, 0, 27, 30, 84, 79, 86, 22, 97, 100, 63, 95, 60, 34, 1, 71, 0, 15, 81, 68, 6, 4, 91, 40, 87, 0, 9, 59, 81, 83, 102, 21]

    for i in range(len(unk_str0)):
        if unk_arr0[i] != ord(unk_str2[i]):
            exit(0)

    print("\nCorrect Flag!\n")

if __name__ == "__main__":
    main()

```
then solving it 
```
func2_result_ord=[32, 0, 27, 30, 84, 79, 86, 22, 97, 100, 63, 95, 60, 34, 1, 71, 0, 15, 81, 68, 6, 4, 91, 40, 87, 0, 9, 59, 81, 83, 102, 21]
flag_len=len(func2_result_ord)
func2_res_in_aray_from = [''] * flag_len
j=0
for i in range(0,flag_len,4):
    func2_res_in_aray_from[j]='loop1 value with j'
    func2_res_in_aray_from[j+1]="loop1 value with j+1"
    j+=2
for i in range(2, flag_len, 4):
        func2_res_in_aray_from[j] = "loop2 value with j"
        func2_res_in_aray_from[j + 1] ="loop 2 value with j+1"
        j += 2
for i in range(len(func2_res_in_aray_from)):
    print(i,func2_res_in_aray_from[i])

```
- with this code we see that the first 0-15 comes from loop1 and 16-31 from loop2
## deobfuscation of code
```
import base64

def func_1(user_input, shadow_string):
    flag_len = len(user_input)
   

    fun1_result = bytearray(user_input, 'utf-8')

    for i in range(flag_len):
        fun1_result[i] = fun1_result[i] ^ ord(shadow_string[i % 10])

    return fun1_result.decode('utf-8')

def func_2(fun1_result):
    flag_len = len(fun1_result)
    func2_res_in_aray_from = [''] * flag_len

    j = 0

    for i in range(0, flag_len , 4):
        func2_res_in_aray_from[j] = fun1_result[i]
        func2_res_in_aray_from[j + 1] = fun1_result[i + 1]
        j += 2

    for i in range(2, flag_len, 4):
        func2_res_in_aray_from[j] = fun1_result[i]
        func2_res_in_aray_from[j + 1] = fun1_result[i + 1]
        j += 2

    return ''.join(func2_res_in_aray_from)

def main():
    shadow_string = 'Shadow2024'
    user_input = input("Enter the input: ")

    fun1_result = func_1(user_input, shadow_string)

    fun2_result = func_2(fun1_result)

    constants_array = [32, 0, 27, 30, 84, 79, 86, 22, 97, 100, 63, 95, 60, 34, 1, 71, 0, 15, 81, 68, 6, 4, 91, 40, 87, 0, 9, 59, 81, 83, 102, 21]

    for i in range(len(user_input)):
        if constants_array[i] != ord(fun2_result[i]):
            exit(0)

    print("\nCorrect Flag!\n")

if __name__ == "__main__":
    main()

```
## from final array to getting the result of func1(how mappingn between final array and func1 result happened)
```
func2_result_ord=[32, 0, 27, 30, 84, 79, 86, 22, 97, 100, 63, 95, 60, 34, 1, 71, 0, 15, 81, 68, 6, 4, 91, 40, 87, 0, 9, 59, 81, 83, 102, 21]
flag_len=len(func2_result_ord)
func2_res_in_aray_from = [''] * flag_len
j=0
new_array=[''] * flag_len
new_array_index=0
for i in range(0,flag_len,4):
    func2_res_in_aray_from[j]='loop1 value with j with i='+str(i)
    new_array[new_array_index]=i
    new_array_index+=1
    func2_res_in_aray_from[j+1]="loop1 value with j+1 with i="+str(i+1)
    new_array[new_array_index]=i+1
    new_array_index+=1
    j+=2
for i in range(2, flag_len, 4):
        func2_res_in_aray_from[j] = "loop2 value with j with i="+str(i)
        new_array[new_array_index]=i
        new_array_index+=1
        func2_res_in_aray_from[j + 1] ="loop 2 value with j+1 with i="+str(i+1)
        new_array[new_array_index]=i+1
        new_array_index+=1
        j += 2
for i in range(len(func2_res_in_aray_from)):
    print(i,func2_res_in_aray_from[i])
# for i in new_array:
#      print(i,end=' ')
print(new_array)
final_need=[32, 0, 27, 30, 84, 79, 86, 22, 97, 100, 63, 95, 60, 34, 1, 71, 0, 15, 81, 68, 6, 4, 91, 40, 87, 0, 9, 59, 81, 83, 102, 21]
'''
func1 res array=?
final_need[0]=func1 res array[new_aray[0]]
final_need[1]=func1 res array[new_aray[1]]

'''
```
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/937174db-1915-4a71-ba19-34d59b1fdc7b)

### the final step
```
final_need=[32, 0, 27, 30, 84, 79, 86, 22, 97, 100, 63, 95, 60, 34, 1, 71, 0, 15, 81, 68, 6, 4, 91, 40, 87, 0, 9, 59, 81, 83, 102, 21]
function1_res_mapping=[0, 1, 4, 5, 8, 9, 12, 13, 16, 17, 20, 21, 24, 25, 28, 29, 2, 3, 6, 7, 10, 11, 14, 15, 18, 19, 22, 23, 26, 27, 30, 31]
#final need[x]=func1_result[function1_res_mapping[x]]
func1_result=[''] * 32

#func1_res[x]=
for i in range(len(function1_res_mapping)):
    func1_result[function1_res_mapping[i]]=final_need[i]
# print(func1_result)
#[32, 0, 0, 15, 27, 30, 81, 68, 84, 79, 6, 4, 86, 22, 91, 40, 97, 100, 87, 0, 63, 95, 9, 59, 60, 34, 81, 83, 1, 71, 102, 21]
answer_array=[''] * 32
shadow_string = 'Shadow2024'
for i in range(32):
    answer_array[i] = chr(func1_result[i] ^ ord(shadow_string[i % 10]))

# print("answer array is ",answer_array)
ans="".join(answer_array)
print("flag is ",ans)

#x=y^z
#x^z=>y
```
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/a31ad236-77e3-4121-968f-fadbb6060494)
flag is  shaktictf{Ul7r4_STe4l7h_SUcc3s5}
