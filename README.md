# 12Riven_Chinese_Findings

# Table of Contents
1.  [Preamble](#preamble)
2.  [Parsing Commands](#parsing-commands)
3.  [Function 0x0044f2d0](#function-0x0044f2d0)
4.  [Command 0x00](#command-0x00)
5.  [Command 0x01](#command-0x01)
6.  [Command 0x02](#command-0x02)
7.  [Command 0x03](#command-0x03)
8.  [Command 0x06](#command-0x06)
9.  [Command 0x07](#command-0x07)
10. [Command 0x08](#command-0x08)
11. [Command 0x09 extGoto](#command-0x09-0x0b)
12. [Command 0x0A extCall](#command-0x0a-0x0c)
13. [Command 0x0B extGoto](#command-0x09-0x0b)
14. [Command 0x0C extCall](#command-0x0a-0x0c)
15. [Command 0x0D return](#command-0x0d) 
16. [Command 0x0E Thread](#command-0x0e)
17. [Command 0x0F](#command-0x0f)
18. [Command 0x10](#command-0x10)
19. [Command 0x11](#command-0x11)
20. [Command 0x12](#command-0x12)
21. [Command 0x13](#command-0x13)
22. [Command 0x14 skipWait](#command-0x14)
23. [Command 0x15 keyWait](#command-0x15)
24. [Command 0x16](#command-0x16)
25. [Command 0x17](#command-0x17)
26. [Command 0x18 msg_disp2](#command-0x18)
27. [Command 0x1A window](#command-0x1a)
28. [Command 0x1C selectP](#command-0x1c)
29. [Command 0x1D select2](#command-0x1d)
30. [Command 0x1F mesSync](#command-0x1f)
31. [Command 0x20 screenMode](#command-0x20)
32. [Command 0x21 setSavePoint](#command-0x21)
33. [Command 0x22 clearSavePoint](#command-0x22)
34. [Command 0x23 setPrevPoint](#command-0x23)
35. [Command 0x24 mesLog](#command-0x24)
36. [Command 0x25 autoStart](#command-0x25)
37. [Command 0x26 autoStop](#command-0x26)
38. [Command 0x27 quickSave](#command-0x27)
39. [Command 0x28 titleDisplay](#command-0x28)
40. [Command 0x29 dateDisplay](#command-0x29)
41. [Command 0x2B locationDisplay](#command-0x2b)
42. [Command 0x2C getOptions](#command-0x02c)
43. [Command 0x2D setIcon](#command-0x2e)
44. [Command 0x2E menuEnable](#command-0x2e)
45. [Command 0x2F menuDisable](#command-0x02f)
46. [Command 0x30 fadeOut](#command-0x30)
47. [Command 0x31 fadeOutStop](#command-0x31-0x33)
48. [Command 0x32 fadeOutStart](#command-0x32)
49. [Command 0x33 charErase](#command-0x33)
50. [Command 0x34 fadeWait](#command-0x34)
51. [Command 0x36 fadePri](#command-0x036)
52. [Command 0x38 filtIn](#command-0x38)
53. [Command 0x39 filtOut](#command-0x39)
54. [Command 0x3A filtInStart](#command-0x3a)
55. [Command 0x3E filtInPri](#command-0x3e)
56. [Command 0x40 charInit](#command-0x40)
57. [Command 0x42 charDisplay](#command-0x42)
58. [Command 0x44](#command-0x44)
59. [Command 0x45](#command-0x45)
60. [Command 0x46](#command-0x46)
61. [Command 0x47](#command-0x47)
62. [Command 0x48](#command-0x48)
63. [Command 0x49](#command-0x49)
64. [Command 0x4A](#command-0x4a)
65. [Command 0x4B](#command-0x4b)
66. [Command 0x4C](#command-0x4c)
67. [Command 0x4D](#command-0x4d)
68. [Command 0x50 charNo](#command-0x50)
69. [Command 0x51 charOn](#command-0x51)
70. [Command 0x52 charPri](#command-0x52)
71. [Command 0x53 charAnimation](#command-0x53)
72. [Command 0x55 charSwap](#command-0x55)
73. [Command 0x56 charShadow / charReturn](#command-0x56-0x57)
74. [Command 0x57 charShadow / charReturn](#command-0x56-0x57)
75. [Command 0x59 charAttack](#command-0x59)
76. [Command 0x5F getBackground](#command-0x5f)
77. [Command 0x60 objInit](#command-0x60)
78. [Command 0x62 objDisplay](#command-0x62)
79. [Command 0x63 objErase](#command-0x63)
80. [Command 0x64](#command-0x64)
81. [Command 0x65](#command-0x65)
82. [Command 0x66](#command-0x66)
83. [Command 0x67](#command-0x67)
84. [Command 0x68](#command-0x68)
85. [Command 0x69](#command-0x69)
86. [Command 0x6A](#command-0x6a)
87. [Command 0x6B](#command-0x6b)
88. [Command 0x6C](#command-0x6c)
89. [Command 0x6D](#command-0x6d)
90. [Command 0x6E](#command-0x6e)
91. [Command 0x6F](#command-0x6f)
92. [Command 0x70 objNo](#command-0x70)
93. [Command 0x71 objOn](#command-0x71)
94. [Command 0x72 objPri](#command-0x72)
95. [Command 0x73 objAnimate](#command-0x73)
96. [Command 0x74 objSort](#command-0x74)
97. [Command 0x75 objSwap](#command-0x75)
98. [Command 0x80 faceInit](#command-0x80)
99. [Command 0x82 faceDisplay](#command-0x82)
100. [Command 0x83 faceErase](#command-0x83)
101. [Command 0x84 facePosition](#command-0x84)
102. [Command 0x85 faceAutoPosition](#command-0x85)
103. [Command 0x88 faceNo](#command-0x88)
104. [Command 0x89 faceon](#command-0x89)
105. [Command 0x8A facePri](#command-0x8a)
106. [Command 0xF8 mesLogSave](#command-0xf8)
    

## Preamble
The following observations are made inside the chinese 12Riven.exe. It is highly likely that the same kind of structures are also found
inside the japanese copy of the game, just at different offsets. Apart from encoding, the game scripts are cross compatible.

Any addresses in the follwing are the absoulte addresses inside the hex dump of the exe. The game is loded at `0x400000`, so just
add the relative offset to get the offsets that Ghira would be working with. For example, the command array in Ghira would be
at location `0x4F4984`.

## Parsing Commands
Starting at location `0x0F4984`, there is an array located that holds a number of structs.

```cpp
struct commands {
  uint32_t commandByte, // a command is repesentet by a singe byte
  commandFunction function, //function pointer
  char* commandName,
}
```

The struct is parsed by a function I called `match_command_to_function`, found at `0x04ef30`.

```cpp
bool match_command_to_function(byte *command, undefined4 *o_functionPointeer)
{
  int index;
  ushort *puVar1;
  
  index = 0;
  if (0 < _endOfCommandStructs) {
    puVar1 = &commandStructBegin;
    do {
      if ((ushort)*command == *puVar1) {
        *o_functionPointeer = &commandStructBegin + index * 8;
        return ((&DAT_004f498c)[index * 4] & _DAT_0095f6c0) == 0;
      }
      index = index + 1;
      puVar1 = puVar1 + 8;
    } while (index < _endOfCommandStructs);
  }
  *o_functionPointeer = 0;
  return false;
}
```
The command matcher takes the byte from the game script and will translate it to a function pointer from the command array.

The command function pointe looks like this
```cpp
undefined4 commandfunction(int *param_1, undefined4 param_2, undefined4 param_3, int *param_4)
```
They can return a value, and they take for params. IIRC the pointer of param_1 will point to the beignning of the current game script and param_3 is the
offset, so the command can parse its param from the script itself.

Some decompiled commands seem to take no params, I think that is because the params are not used inside the function.

## Function 0x0044f2d0

```cpp
int FUN_0044f2d0(undefined2 *param_1,uint *param_2)

{
  byte bVar1;
  ushort uVar2;
  ushort uVar3;
  uint uVar4;
  uint *puVar5;
  int local_4;
  
  *param_2 = 0;
  local_4 = 0;
  uVar2 = commandArgParser(*param_1);
  uVar3 = commandArgParser(param_1[1]);
  bVar1 = *(byte *)(param_1 + 2);
  puVar5 = param_2;
  while( true ) {
    if (7 < bVar1) {
      return -1;
    }
    switch((&switchD_0044f320::switchdataD_0044f3f4)[bVar1]) {
    case (undefined *)0x44f327:
      uVar4 = (uint)(uVar2 == uVar3);
      break;
    case (undefined *)0x44f333:
      uVar4 = (uint)(uVar2 != uVar3);
      break;
    case (undefined *)0x44f33f:
      uVar4 = (uint)((short)uVar2 <= (short)uVar3);
      break;
    case (undefined *)0x44f34b:
      uVar4 = (uint)((short)uVar3 <= (short)uVar2);
      break;
    case (undefined *)0x44f357:
      uVar4 = (uint)((short)uVar2 < (short)uVar3);
      break;
    case (undefined *)0x44f363:
      uVar4 = (uint)((short)uVar3 < (short)uVar2);
      break;
    case (undefined *)0x44f36f:
      uVar4 = (uint)(short)(uVar3 & uVar2);
      break;
    case (undefined *)0x44f379:
      uVar4 = (uint)(short)(uVar3 | uVar2);
    }
    if (local_4 == 0) {
      *param_2 = uVar4;
    }
    else if (puVar5 == (uint *)0x10) {
      *param_2 = *param_2 & uVar4;
    }
    else {
      if (puVar5 != (uint *)0x11) {
        return -1;
      }
      *param_2 = *param_2 | uVar4;
    }
    local_4 = local_4 + 1;
    if (*(byte *)((int)param_1 + 5) == 0) break;
    puVar5 = (uint *)(uint)*(byte *)((int)param_1 + 5);
    uVar2 = commandArgParser(param_1[3]);
    uVar3 = commandArgParser(param_1[4]);
    bVar1 = *(byte *)(param_1 + 5);
    param_1 = param_1 + 3;
  }
  return local_4;
```

Function 0x0044f2d0 is called by [command 0x06](#command-0x06) and [command 0x07](#command-0x07). The difference between the two is 
that 0x06 does an copmarison for equality while 0x07 does one for inequality.


## Command 0x00
### Official name: (N/A)
### My guess: NOP
### Code
  
```cpp
undefined4 command_0x0(void)
{
  int *in_stack_00000010;
  
  *in_stack_00000010 =
       (uint)(byte)(&scriptCommandLength_0x0097fb81)[*in_stack_00000010] + *in_stack_00000010;
  return 1;
}
```

## Command 0x01
### Official name: (N/A)
### My guess: NOP
### Code
  
```cpp
undefined4 command_0x0(void)
{
  int *in_stack_00000010;
  
  *in_stack_00000010 =
       (uint)(byte)(&scriptCommandLength_0x0097fb81)[*in_stack_00000010] + *in_stack_00000010;
  return 1;
}
```

## Command 0x02
### Official name: (N/A)
### My guess: NOP
### Code
  
```cpp
undefined4 command_0x02(void)
{
  short sVar1;
  int *in_stack_00000010;
  
  sVar1 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + *in_stack_00000010));
  *in_stack_00000010 = (int)sVar1;
  return 1;
}
```

## Command 0x03
### Official name: (N/A)
### My guess: (N/A)
### Code
  
```cpp
undefined4 command_0x03(void)
{
  ushort uVar1;
  uint uVar2;
  uint *in_stack_00000010;
  
  uVar2 = *in_stack_00000010;
  if (DAT_0095f4b2 != 0) {
    FID_conflict:_wprintf("Error Therad call\n");
    do {
                    /* WARNING: Do nothing block with infinite loop */
    } while( true );
  }
  if (0xf < DAT_0095f4a2) {
    FID_conflict:_wprintf("Error Stack Over\n");
    do {
                    /* WARNING: Do nothing block with infinite loop */
    } while( true );
  }
  *(undefined2 *)(&DAT_0095f460 + DAT_0095f4a2) = scriptNameIndex_95f4a4;
  uVar1 = *(ushort *)(&DAT_0097fb82 + uVar2);
  *(ushort *)((int)&DAT_0095f460 + (uint)DAT_0095f4a2 * 4 + 2) =
       (ushort)(byte)(&scriptCommandLength_0x0097fb81)[uVar2] + *(short *)in_stack_00000010;
  DAT_0095f4a2 = DAT_0095f4a2 + 1;
  *in_stack_00000010 = (uint)uVar1;
  return 1;
}
```

## Command 0x06
### Official name: (N/A)
### My guess: (N/A)
### Code
  
```cpp
undefined4 command_0x06(void)

{
  uint uVar1;
  uint *puVar2;
  int iVar3;
  uint *in_stack_00000010;
  
  puVar2 = in_stack_00000010;
  uVar1 = *in_stack_00000010;
  iVar3 = FUN_0044f2d0(&DAT_0097fb84 + uVar1,&stack0x00000010);
  if (iVar3 < 0) {
    return 2;
  }
  if (in_stack_00000010 != (uint *)0x0) {
    *puVar2 = (uint)*(ushort *)(&DAT_0097fb82 + uVar1);
    return 1;
  }
  *puVar2 = *puVar2 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[uVar1];
  return 1;
}
```

## Command 0x07
### Official name: (N/A)
### My guess: (N/A)
### Code
  
```cpp
undefined4 command_0x07(void)
{
  uint uVar1;
  uint *puVar2;
  int iVar3;
  uint *in_stack_00000010;
  
  puVar2 = in_stack_00000010;
  uVar1 = *in_stack_00000010;
  iVar3 = FUN_0044f2d0(&DAT_0097fb84 + uVar1,&stack0x00000010);
  if (iVar3 < 0) {
    return 2;
  }
  if (in_stack_00000010 == (uint *)0x0) {
    *puVar2 = (uint)*(ushort *)(&DAT_0097fb82 + uVar1);
    return 1;
  }
  *puVar2 = *puVar2 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[uVar1];
  return 1;
}
```

## Command 0x08
### Official name: (N/A)
### My guess: (N/A)
### Code
  
```cpp
undefined4 command_0x08(void)

{
  uint uVar1;
  short sVar2;
  short sVar3;
  int iVar4;
  uint *in_stack_00000010;
  
  uVar1 = *in_stack_00000010;
  iVar4 = 0;
  if (*(short *)(&DAT_0097fb84 + uVar1) != 0) {
    do {
      sVar2 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar4 * 4 + uVar1));
      sVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + uVar1));
      if (sVar2 == sVar3) {
        *in_stack_00000010 = (uint)*(ushort *)(&DAT_0097fb88 + iVar4 * 4 + uVar1);
        return 1;
      }
      iVar4 = iVar4 + 1;
    } while (iVar4 < (int)(uint)*(ushort *)(&DAT_0097fb84 + uVar1));
  }
  *in_stack_00000010 = *in_stack_00000010 + (uint)*(ushort *)(&DAT_0097fb84 + uVar1) * 4 + 6;
  return 1;
}
```

## Command 0x09 0x0B
### Official name: extGoto
### My guess: extern goto script
### Description
This command takes a script number as arguments and jumps to this script. On return, the opcode that
comes after the goto call are skiped and the script ends completly and next script is loaded.
### Code
  
```cpp
undefined4
command_0x09_0x0B_extGoto(int *wasVisited,undefined4 param_2,int *param_3,uint *commandOffsetPtr)

{
  short gotoArg;
  int iVar1;
  uint commandOffset;
  
  commandOffset = *commandOffsetPtr;
  if (*wasVisited == 0) {
    gotoArg = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + commandOffset));
    *param_3 = (int)gotoArg;
    gotoArg = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + commandOffset));
    param_3[1] = (int)gotoArg;
    if (*param_3 == -2) {
      if (scriptNameIndex_95f4a4 == 0) {
        *param_3 = 3;
      }
      else {
        *param_3 = scriptNameIndex_95f4a4 - 1;
      }
    }
    else if (*param_3 == -1) {
      *param_3 = scriptNameIndex_95f4a4 + 1;
    }
    scriptNameIndex_95f4a4 = *(ushort *)param_3;
    FUN_0042b6c0(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4);
    *wasVisited = *wasVisited + 1;
  }
  else if (*wasVisited == 1) {
    iVar1 = thunk_FUN_0042a300();
    if (iVar1 != 0) {
      *commandOffsetPtr = (uint)*(ushort *)(&scriptBeginAddress_0x97fb80 + param_3[1] * 2);
      return 2;
    }
  }
  return 0;
}
```

## Command 0x0A 0x0C
### Official name: extCall
### My guess: extern call script
### Description
Like the goto opcode, it takes a script number and jumps to the script. However, on return the 
subsequent opcodes in the calling script are not skipped. I think that this call can also jump to a certain part 
inside the script, but wasn't able to verify this.
### Code
  
```cpp
undefined4
undefined4 command_0x0A_0x0C_extCall(int *param_1,undefined4 param_2,int *param_3,uint *param_4)

{
  undefined2 uVar1;
  uint uVar2;
  short sVar3;
  int iVar4;
  
  uVar2 = *param_4;
  if (*param_1 == 0) {
    if (0xf < DAT_0095f4a2) {
      FID_conflict:_wprintf("Error Stack Over\n");
      do {
                    /* WARNING: Do nothing block with infinite loop */
      } while( true );
    }
    *(ushort *)(&DAT_0095f460 + DAT_0095f4a2) = scriptNameIndex_95f4a4;
    uVar1 = *(undefined2 *)(&DAT_0097fb82 + uVar2);
    *(short *)((int)&DAT_0095f460 + (uint)DAT_0095f4a2 * 4 + 2) = *(short *)param_4 + 6;
    DAT_0095f4a2 = DAT_0095f4a2 + 1;
    sVar3 = commandArgParser(uVar1);
    *param_3 = (int)sVar3;
    sVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + uVar2));
    param_3[1] = (int)sVar3;
    if (*param_3 == -2) {
      if (scriptNameIndex_95f4a4 == 0) {
        *param_3 = 3;
      }
      else {
        *param_3 = scriptNameIndex_95f4a4 - 1;
      }
    }
    else if (*param_3 == -1) {
      *param_3 = scriptNameIndex_95f4a4 + 1;
    }
    scriptNameIndex_95f4a4 = *(ushort *)param_3;
    FUN_0042b6c0(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4);
    *param_1 = *param_1 + 1;
  }
  else if (*param_1 == 1) {
    iVar4 = thunk_FUN_0042a300();
    if (iVar4 != 0) {
      *param_4 = (uint)*(ushort *)(&scriptBeginAddress_0x97fb80 + param_3[1] * 2);
      return 2;
    }
  }
  return 0;
}
```

## Command 0x0D
### Official name: ret
### My guess: marks the end of a script
### Description
When this opcode is read, the game will load the next script. Is at the end of all scripts.
### Code
  
```cpp
undefined4 command_0x0D(void)

{
  int iVar1;
  uint *in_stack_00000010;
  
  DAT_0095f4a2 = DAT_0095f4a2 - 1;
  iVar1 = (uint)DAT_0095f4a2 * 4;
  if (scriptNameIndex_95f4a4 != *(short *)(&DAT_0095f460 + DAT_0095f4a2)) {
    scriptNameIndex_95f4a4 = *(short *)(&DAT_0095f460 + DAT_0095f4a2);
    *in_stack_00000010 = (uint)*(ushort *)((int)&DAT_0095f460 + iVar1 + 2);
    FUN_0042b690(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4);
    return 1;
  }
  *in_stack_00000010 = (uint)*(ushort *)((int)&DAT_0095f460 + iVar1 + 2);
  return 1;
}
```

## Command 0x0D
### Official name: ret
### My guess: marks the end of a script
### Description
When this opcode is read, the game will load the next script. Is at the end of all scripts.
### Code
  
```cpp
undefined4 command_0x0D(void)

{
  int iVar1;
  uint *in_stack_00000010;
  
  DAT_0095f4a2 = DAT_0095f4a2 - 1;
  iVar1 = (uint)DAT_0095f4a2 * 4;
  if (scriptNameIndex_95f4a4 != *(short *)(&DAT_0095f460 + DAT_0095f4a2)) {
    scriptNameIndex_95f4a4 = *(short *)(&DAT_0095f460 + DAT_0095f4a2);
    *in_stack_00000010 = (uint)*(ushort *)((int)&DAT_0095f460 + iVar1 + 2);
    FUN_0042b690(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4);
    return 1;
  }
  *in_stack_00000010 = (uint)*(ushort *)((int)&DAT_0095f460 + iVar1 + 2);
  return 1;
}
```

## Command 0x0E
### Official name: thread
### My guess: Starts a new thread (?)

### Code
```cpp
undefined4 command_0x0E_thread(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)

{
  byte bVar1;
  char cVar2;
  short sVar3;
  int iVar4;
  undefined4 uVar5;
  
  cVar2 = (&DAT_0097fb82)[*param_4];
  if (cVar2 == '\0') {
    iVar4 = *param_4;
    if (*param_1 != 0) {
      return 0;
    }
    sVar3 = *(short *)(&DAT_0097fb84 + iVar4);
    if ((0 < sVar3) && (sVar3 < 0x40)) {
      bVar1 = (&scriptCommandLength_0x0097fb81)[iVar4];
      (&scriptCommandOffsetsArray_0x95f4b4)[sVar3] = (uint)*(ushort *)(&DAT_0097fb86 + iVar4);
      (&commandWasExecuted_0x00522f58)[sVar3 * 0x12] = 0;
      *param_4 = *param_4 + (uint)bVar1;
      return 1;
    }
    FID_conflict:_wprintf("Error Thred ID\n");
    do {
                    /* WARNING: Do nothing block with infinite loop */
    } while( true );
  }
  if (cVar2 == '\x01') {
    uVar5 = FUN_0044f6e0();
    return uVar5;
  }
  if (cVar2 != '\x02') {
    return 0;
  }
  uVar5 = FUN_0044f750();
  return uVar5;
}
```

## Command 0x0F
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x0f(void)

{
  int iVar1;
  short sVar2;
  short sVar3;
  short sVar4;
  uint uVar5;
  uint uVar6;
  uint uVar7;
  short sVar8;
  bool bVar9;
  int *in_stack_00000010;
  
  iVar1 = *in_stack_00000010;
  sVar8 = 0;
  sVar2 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar1));
  sVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar1));
  uVar5 = (uint)sVar3;
  sVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb88 + iVar1));
  sVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb8a + iVar1));
  uVar6 = (uint)sVar4;
  sVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb8c + iVar1));
  if (sVar4 == 1) {
    if (0 < (int)uVar5) {
      sVar8 = (short)(char)(&scriptBeginAddress_0x97fb80)[(int)sVar3 * uVar5 + uVar6 + (int)sVar2];
    }
  }
  else if ((sVar4 == 2) && (1 < (int)uVar5)) {
    uVar7 = uVar5 & 0x80000001;
    bVar9 = uVar7 == 0;
    if ((int)uVar7 < 0) {
      bVar9 = (uVar7 - 1 | 0xfffffffe) == 0xffffffff;
    }
    if (bVar9) {
      uVar7 = uVar6 & 0x80000001;
      bVar9 = uVar7 == 0;
      if ((int)uVar7 < 0) {
        bVar9 = (uVar7 - 1 | 0xfffffffe) == 0xffffffff;
      }
      if (bVar9) {
        sVar8 = *(short *)(&scriptBeginAddress_0x97fb80 + (int)sVar3 * uVar5 + uVar6 + (int)sVar2);
      }
    }
  }
  uVar5 = (uint)*(ushort *)(&DAT_0097fb82 + iVar1);
  if ((ushort)(*(ushort *)(&DAT_0097fb82 + iVar1) + 0x8000) < 0x1000) {
    if ((uVar5 & 0xfff) < 0x800) {
      (&DAT_0095d860)[uVar5 & 0x7ff] = sVar8;
    }
    else {
      (&DAT_0095d560)[uVar5 & 0x7ff] = (byte)sVar8 & 1;
    }
  }
  *in_stack_00000010 = *in_stack_00000010 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}

```

## Command 0x10
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp

undefined4 command_0x10(int *param_1,int *param_2,int *param_3,int *param_4)
{
  int iVar1;
  short sVar2;
  int iVar3;
  undefined4 uVar4;
  
  iVar1 = *param_4;
  if (*param_1 == 0) {
    sVar2 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar1));
    *param_3 = (int)sVar2;
    *param_1 = *param_1 + 1;
  }
  else if (*param_1 != 1) {
    return 0;
  }
  if (((&DAT_0097fb82)[iVar1] & 2) != 0) {
    if ((DAT_0095f6d0 == '\0') ||
       (((DAT_008e12ac & 0xd001) == 0 && (iVar3 = FUN_00481bf0(), iVar3 == 0)))) {
      if ((DAT_0095f6d0 != '\x02') &&
         ((((byte)DAT_008e12b4 & 8) != 0 || (iVar3 = FUN_00481be0(), iVar3 != 0)))) {
        FUN_0040f5e0(0xe,0);
        FUN_0044a2c0(2);
      }
    }
    else {
      if (DAT_0095f6d0 == '\x01') {
        uVar4 = 0xd;
      }
      else {
        uVar4 = 0xf;
      }
      FUN_0040f5e0(uVar4,0);
      FUN_0044a2c0(0);
    }
  }
  if ((((&DAT_0097fb82)[iVar1] & 1) == 0) ||
     (((DAT_008e12ac & 0xa00) == 0 && (DAT_0095f6d0 != '\x02')))) {
    if ((-1 < *param_3) && (iVar3 = *param_3 + -1, *param_3 = iVar3, iVar3 < 1)) {
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
      *param_2 = *param_2 + 1;
      return 2;
    }
    return 0;
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  if (DAT_042b52d8 != '\0') {
    *param_2 = *param_2 + 1;
    return 1;
  }
  iVar1 = *param_2;
  if (2 < iVar1) {
    *param_2 = iVar1 + 1;
    return 2;
  }
  *param_2 = iVar1 + 1;
  return 1;
}
```

## Command 0x11
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp

undefined4 command_0x11(int *param_1,undefined4 param_2,undefined4 *param_3,int *param_4)
{
  int iVar1;
  uint uVar2;
  
  iVar1 = *param_4;
  if (*param_1 == 0) {
    *param_3 = 0;
    *param_1 = *param_1 + 1;
  }
  else if (*param_1 != 1) {
    return 0;
  }
  uVar2 = (&DAT_008e12b4)[(uint)*(ushort *)(&DAT_0097fb82 + iVar1) * 0x7d];
  param_4._0_2_ = 0;
  if ((uVar2 & 0x110010) != 0) {
    param_4._0_2_ = 8;
  }
  if ((uVar2 & 0x440040) != 0) {
    param_4._0_2_ = (ushort)param_4 | 2;
  }
  if ((uVar2 & 0x880080) != 0) {
    param_4._0_2_ = (ushort)param_4 | 1;
  }
  if ((uVar2 & 0x220020) != 0) {
    param_4._0_2_ = (ushort)param_4 | 4;
  }
  if ((uVar2 & 0x2000) != 0) {
    param_4._0_2_ = (ushort)param_4 | 0x10;
  }
  if ((uVar2 & 2) != 0) {
    param_4._0_2_ = (ushort)param_4 | 0x10;
  }
  if ((uVar2 & 4) != 0) {
    param_4._0_2_ = (ushort)param_4 | 0x10;
  }
  if ((uVar2 & 0x4000) != 0) {
    param_4._0_2_ = (ushort)param_4 | 0x20;
  }
  if ((uVar2 & 0x8000) != 0) {
    param_4._0_2_ = (ushort)param_4 | 0x40;
  }
  if ((uVar2 & 0x1000) != 0) {
    param_4._0_2_ = (ushort)param_4 | 0x80;
  }
  if ((uVar2 & 0x400) != 0) {
    param_4._0_2_ = (ushort)param_4 | 0x100;
  }
  if ((uVar2 & 0x100) != 0) {
    param_4._0_2_ = (ushort)param_4 | 0x200;
  }
  if ((uVar2 & 0x800) != 0) {
    param_4._0_2_ = (ushort)param_4 | 0x400;
  }
  if ((uVar2 & 0x200) != 0) {
    param_4._0_2_ = (ushort)param_4 | 0x800;
  }
  if (((ushort)param_4 & *(ushort *)(&DAT_0097fb86 + iVar1)) == 0) {
    return 0;
  }
  FUN_0044f060(*(undefined2 *)(&DAT_0097fb84 + iVar1),
               (ushort)param_4 & *(ushort *)(&DAT_0097fb86 + iVar1));
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 2;
}
```

## Command 0x12
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x12(int *param_1,undefined4 param_2,undefined4 *param_3,int *param_4)
{
  int iVar1;
  ushort uVar2;
  uint uVar3;
  
  iVar1 = *param_4;
  if (*param_1 == 0) {
    *param_3 = 0;
    *param_1 = *param_1 + 1;
  }
  else if (*param_1 != 1) {
    return 0;
  }
  uVar2 = 0;
  if (*(short *)(&DAT_0097fb88 + iVar1) == 0) {
    uVar3 = (&DAT_008e12ac)[(uint)*(ushort *)(&DAT_0097fb82 + iVar1) * 0x7d];
  }
  else {
    uVar3 = (&DAT_008e12b4)[(uint)*(ushort *)(&DAT_0097fb82 + iVar1) * 0x7d];
  }
  if ((uVar3 & 0x110010) != 0) {
    uVar2 = 8;
  }
  if ((uVar3 & 0x440040) != 0) {
    uVar2 = uVar2 | 2;
  }
  if ((uVar3 & 0x880080) != 0) {
    uVar2 = uVar2 | 1;
  }
  if ((uVar3 & 0x220020) != 0) {
    uVar2 = uVar2 | 4;
  }
  if ((uVar3 & 0x2000) != 0) {
    uVar2 = uVar2 | 0x10;
  }
  if ((uVar3 & 2) != 0) {
    uVar2 = uVar2 | 0x10;
  }
  if ((uVar3 & 4) != 0) {
    uVar2 = uVar2 | 0x10;
  }
  if ((uVar3 & 0x4000) != 0) {
    uVar2 = uVar2 | 0x20;
  }
  if ((uVar3 & 0x8000) != 0) {
    uVar2 = uVar2 | 0x40;
  }
  if ((uVar3 & 0x1000) != 0) {
    uVar2 = uVar2 | 0x80;
  }
  if ((uVar3 & 0x400) != 0) {
    uVar2 = uVar2 | 0x100;
  }
  if ((uVar3 & 0x100) != 0) {
    uVar2 = uVar2 | 0x200;
  }
  if ((uVar3 & 0x800) != 0) {
    uVar2 = uVar2 | 0x400;
  }
  if ((uVar3 & 0x200) != 0) {
    uVar2 = uVar2 | 0x800;
  }
  uVar3 = (uint)*(ushort *)(&DAT_0097fb84 + iVar1);
  if ((ushort)(*(ushort *)(&DAT_0097fb84 + iVar1) + 0x8000) < 0x1000) {
    if ((uVar3 & 0xfff) < 0x800) {
      (&DAT_0095d860)[uVar3 & 0x7ff] = *(ushort *)(&DAT_0097fb86 + iVar1) & uVar2;
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
      return 1;
    }
    (&DAT_0095d560)[uVar3 & 0x7ff] = (byte)(*(ushort *)(&DAT_0097fb86 + iVar1) & uVar2) & 1;
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x13
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x13(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  undefined2 uVar1;
  int iVar2;
  
  iVar2 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  if (DAT_0095f6d0 != '\x02') {
    uVar1 = *(undefined2 *)(&DAT_0097fb82 + iVar2);
  }
  else {
    uVar1 = *(undefined2 *)(&DAT_0097fb82 + iVar2);
  }
  FUN_0044f060(uVar1,DAT_0095f6d0 == '\x02');
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
  return 1;
}
```

## Command 0x14
### Official name: skipWait
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x14_skipWait(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  int iVar1;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  if (*(ushort *)(&DAT_0097fb82 + iVar1) == 0) {
    (&DAT_0095f5b8)[DAT_0095f4b2] = 0;
  }
  else {
    (&DAT_0095f5b8)[DAT_0095f4b2] = (uint)*(ushort *)(&DAT_0097fb82 + iVar1);
    if (DAT_0095f4b2 == 0) {
      _DAT_0095f6b8 = *(undefined2 *)(&DAT_0097fb84 + iVar1);
      DAT_0095f6ba = DAT_0095f4a2;
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
      return 1;
    }
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x15
### Official name: keyWait
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x15_keyWait(int *param_1,undefined4 param_2,undefined4 *param_3,int *param_4)
{
  int iVar1;
  short sVar2;
  
  iVar1 = *param_4;
  if (*param_1 == 0) {
    *param_3 = 0;
    sVar2 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar1));
    param_3[2] = (int)sVar2 << 0x10;
    sVar2 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar1));
    param_3[3] = (int)sVar2 << 0x10;
    FUN_00439010();
    *(undefined *)(param_3 + 1) = 1;
    *param_1 = *param_1 + 1;
  }
  else if (*param_1 != 1) {
    return 0;
  }
  FUN_00439030(param_3 + 2,0x3f800000);
  if ((DAT_008e12b4 & 0x2006) == 0) {
    return 0;
  }
  FUN_0040f5e0(10,0);
  *(undefined *)(param_3 + 1) = 0;
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 2;
}
```

## Command 0x16
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x16(void)

{
  char cVar1;
  int iVar2;
  ushort uVar3;
  ushort uVar4;
  uint uVar5;
  uint uVar6;
  uint uVar7;
  byte *pbVar8;
  char *pcVar9;
  undefined4 *puVar10;
  short sVar11;
  undefined4 *puVar12;
  byte bVar13;
  ushort uVar14;
  uint uVar15;
  ushort *puVar16;
  undefined4 *puVar17;
  undefined4 *puVar18;
  int *in_stack_00000010;
  ushort local_8;
  uint local_4;
  
  iVar2 = *in_stack_00000010;
  uVar5 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
  uVar5 = uVar5 & 0xffff;
  uVar4 = *(ushort *)(&DAT_0097fb84 + iVar2);
  if ((ushort)(uVar4 + 0x8000) < 0x1000) {
    sVar11 = 2 - (ushort)((uVar4 & 0xfff) < 0x800);
  }
  else {
    sVar11 = 0;
  }
  uVar6 = uVar4 & 0x7ff;
  uVar7 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar2));
  uVar15 = uVar7 & 0xffff;
  if ((byte)(&scriptCommandLength_0x0097fb81)[iVar2] < 10) {
    local_4 = 0;
  }
  else {
    local_4 = commandArgParser(*(undefined2 *)(&DAT_0097fb88 + iVar2));
    local_4 = local_4 & 0xffff;
  }
  uVar4 = (ushort)local_4;
  uVar14 = (ushort)uVar15;
  local_8 = (ushort)uVar5;
  if (sVar11 == 0) {
    switch((&DAT_0097fb82)[iVar2]) {
    case 0xe:
      if (0x3f < (short)local_8) {
        FID_conflict:_wprintf("Calc error\n");
      }
      if (0x1f < (short)uVar14) {
        FID_conflict:_wprintf("Calc error\n");
      }
      *(ushort *)((int)&DAT_0095e460 + ((short)local_8 * 0x20 + (int)(short)uVar14) * 2) = uVar4;
      break;
    case 0xf:
      if (0x3f < (short)local_8) {
        FID_conflict:_wprintf("Calc error\n");
      }
      if (0x1f < (short)uVar14) {
        FID_conflict:_wprintf("Calc error\n");
      }
      *(char *)((int)&DAT_0095dc60 + (int)(short)uVar14 + (short)local_8 * 0x20) = (char)local_4;
      break;
    case 0x25:
      FUN_0044f7b0(&scriptBeginAddress_0x97fb80 + (short)local_8,
                   &scriptBeginAddress_0x97fb80 + (short)uVar14,(int)(short)uVar4);
      break;
    case 0x50:
      pcVar9 = &scriptBeginAddress_0x97fb80 + (short)uVar14;
      do {
        cVar1 = *pcVar9;
        pcVar9[(int)(short)local_8 - (int)(short)uVar14] = cVar1;
        pcVar9 = pcVar9 + 1;
      } while (cVar1 != '\0');
      break;
    case 0x51:
      puVar10 = (undefined4 *)(&scriptBeginAddress_0x97fb80 + (short)uVar14);
      puVar12 = puVar10;
      do {
        cVar1 = *(char *)puVar12;
        puVar12 = (undefined4 *)((int)puVar12 + 1);
      } while (cVar1 != '\0');
      puVar18 = (undefined4 *)((short)local_8 + 0x97fb7f);
      do {
        pcVar9 = (char *)((int)puVar18 + 1);
        puVar18 = (undefined4 *)((int)puVar18 + 1);
      } while (*pcVar9 != '\0');
      puVar17 = puVar10;
      for (uVar5 = (uint)((int)puVar12 - (int)puVar10) >> 2; uVar5 != 0; uVar5 = uVar5 - 1) {
        *puVar18 = *puVar17;
        puVar17 = puVar17 + 1;
        puVar18 = puVar18 + 1;
      }
      for (uVar5 = (int)puVar12 - (int)puVar10 & 3; uVar5 != 0; uVar5 = uVar5 - 1) {
        *(undefined *)puVar18 = *(undefined *)puVar17;
        puVar17 = (undefined4 *)((int)puVar17 + 1);
        puVar18 = (undefined4 *)((int)puVar18 + 1);
      }
    }
    goto switchD_0044fcef_caseD_10;
  }
  bVar13 = (byte)uVar15;
  if (sVar11 != 1) {
    if (sVar11 != 2) {
switchD_0044f9e9_caseD_1b:
      return 2;
    }
    if (uVar6 < 0x300) {
      puVar12 = (undefined4 *)&DAT_0095d560;
      pbVar8 = &DAT_0095d560 + uVar6;
    }
    else {
      if (0x1f < (int)(uVar6 - 0x300)) {
        FID_conflict:_wprintf("Calc error\n");
      }
      puVar12 = &DAT_0095dc60 + DAT_0095f4b2 * 8;
      pbVar8 = (byte *)((int)&DAT_0095dc60 + (uVar6 - 0x300) + DAT_0095f4b2 * 0x20);
    }
    local_8._0_1_ = (byte)uVar5;
    switch((&DAT_0097fb82)[iVar2]) {
    case 0:
      *pbVar8 = bVar13;
      break;
    default:
      goto switchD_0044f9e9_caseD_1b;
    case 6:
      *pbVar8 = bVar13 & (byte)local_8;
      break;
    case 7:
      *pbVar8 = bVar13 | (byte)local_8;
      break;
    case 8:
      *pbVar8 = bVar13 ^ (byte)local_8;
      break;
    case 9:
      *pbVar8 = ~bVar13;
      break;
    case 0x1a:
      *pbVar8 = (&DAT_0095d560)[(short)uVar14];
      break;
    case 0x1b:
      *(byte *)((int)(short)local_8 + (int)puVar12) = bVar13;
    }
    goto switchD_0044fcef_caseD_10;
  }
  if (uVar6 < 0x200) {
    puVar12 = (undefined4 *)&DAT_0095d860;
    puVar16 = &DAT_0095d860 + uVar6;
  }
  else {
    if (0x1f < (int)(uVar6 - 0x200)) {
      FID_conflict:_wprintf("Calc error\n");
    }
    puVar12 = &DAT_0095e460 + DAT_0095f4b2 * 0x10;
    puVar16 = (ushort *)((int)&DAT_0095e460 + (DAT_0095f4b2 * 0x20 + (uVar6 - 0x200)) * 2);
  }
  switch((&DAT_0097fb82)[iVar2]) {
  case 0:
    *puVar16 = uVar14;
    break;
  case 1:
    *puVar16 = uVar14 + local_8;
    break;
  case 2:
    *puVar16 = local_8 - uVar14;
    break;
  case 3:
    *puVar16 = uVar14 * local_8;
    break;
  case 4:
    *puVar16 = (short)local_8 / (short)uVar14;
    break;
  case 5:
    *puVar16 = (short)local_8 % (short)uVar14;
    break;
  case 6:
    *puVar16 = uVar14 & local_8;
    break;
  case 7:
    *puVar16 = uVar14 | local_8;
    break;
  case 8:
    *puVar16 = uVar14 ^ local_8;
    break;
  case 9:
    *puVar16 = ~uVar14;
    break;
  case 10:
    *puVar16 = (ushort)((int)(short)uVar14 * (int)(short)local_8 +
                        ((int)(short)uVar14 * (int)(short)local_8 >> 0x1f & 0xffU) >> 8);
    break;
  case 0xb:
    *puVar16 = (ushort)(((int)(short)local_8 << 8) / (int)(short)uVar14);
    break;
  case 0xc:
    uVar3 = local_8 + uVar14;
    if ((short)uVar4 < (short)(local_8 + uVar14)) {
      uVar3 = uVar4;
    }
    *puVar16 = uVar3;
    break;
  case 0xd:
    uVar3 = local_8 - uVar14;
    if ((short)(local_8 - uVar14) < (short)uVar4) {
      uVar3 = uVar4;
    }
    *puVar16 = uVar3;
    break;
  case 0xe:
    if (0x3f < (short)local_8) {
      FID_conflict:_wprintf("Calc error\n");
    }
    if (0x1f < (short)uVar14) {
      FID_conflict:_wprintf("Calc error\n");
    }
    *(ushort *)((int)&DAT_0095e460 + ((short)local_8 * 0x20 + (int)(short)uVar14) * 2) = uVar4;
    break;
  case 0xf:
    if (0x3f < (short)local_8) {
      FID_conflict:_wprintf("Calc error\n");
    }
    if (0x1f < (short)uVar14) {
      FID_conflict:_wprintf("Calc error\n");
    }
    *(char *)((int)&DAT_0095dc60 + (int)(short)uVar14 + (short)local_8 * 0x20) = (char)local_4;
    break;
  case 0x10:
    *puVar16 = (ushort)(byte)(&scriptBeginAddress_0x97fb80)[uVar15];
    break;
  case 0x11:
    *puVar16 = *(ushort *)(&scriptBeginAddress_0x97fb80 + uVar15);
    break;
  case 0x12:
    *puVar16 = (ushort)(byte)(&scriptBeginAddress_0x97fb80)[uVar15 + local_4];
    break;
  case 0x13:
    *puVar16 = *(ushort *)(&scriptBeginAddress_0x97fb80 + uVar15 + local_4);
    break;
  case 0x14:
    uVar4 = commandArgParser(uVar15);
    *puVar16 = uVar4;
    break;
  case 0x15:
    FUN_0044f060(uVar5,(int)(short)uVar14);
    *puVar16 = local_8;
    break;
  case 0x16:
    *puVar16 = *(ushort *)(&DAT_0097fb86 + iVar2);
    break;
  case 0x17:
    *puVar16 = *(short *)(&DAT_0097fb86 + iVar2) + local_8;
    break;
  case 0x18:
    *puVar16 = (&DAT_0095d860)[(short)uVar14];
    break;
  case 0x19:
    *(ushort *)((int)puVar12 + (short)local_8 * 2) = uVar14;
    break;
  case 0x1a:
    *puVar16 = (ushort)(byte)(&DAT_0095d560)[(short)uVar14];
    break;
  default:
    goto switchD_0044f9e9_caseD_1b;
  case 0x20:
    uVar4 = FUN_004679a0((int)(short)uVar14);
    *puVar16 = uVar4;
    break;
  case 0x21:
    FUN_00467910((int)(short)uVar14 << 6);
    goto LAB_0044fbcd;
  case 0x22:
    FUN_00467930((int)(short)uVar14 << 6);
LAB_0044fbcd:
    uVar4 = FUN_004b9d10();
    *puVar16 = uVar4;
    break;
  case 0x23:
    *puVar16 = (ushort)(uVar5 << ((byte)uVar7 & 0x1f));
    break;
  case 0x24:
    *puVar16 = (short)local_8 >> (bVar13 & 0x1f);
    break;
  case 0x25:
    FUN_0044f7b0(&scriptBeginAddress_0x97fb80 + (short)local_8,
                 &scriptBeginAddress_0x97fb80 + (short)uVar14,(int)(short)uVar4);
  }
switchD_0044fcef_caseD_10:
  *in_stack_00000010 = *in_stack_00000010 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
  return 1;
}
```

## Command 0x17
### Official name: (N?A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x17(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  int iVar1;
  short sVar2;
  undefined4 uVar3;
  int iVar4;
  
  iVar1 = *param_4;
  if (*param_1 == 0) {
    sVar2 = commandArgParser(*(undefined2 *)(&DAT_0097fb8a + iVar1));
    iVar4 = (int)sVar2;
    if (iVar4 < 0) {
      iVar4 = 0;
    }
    sVar2 = commandArgParser(*(undefined2 *)(&DAT_0097fb8c + iVar1));
    if (sVar2 < iVar4) {
      sVar2 = commandArgParser(*(undefined2 *)(&DAT_0097fb8c + iVar1));
      iVar4 = (int)sVar2;
    }
    sVar2 = commandArgParser(*(undefined2 *)(&DAT_0097fb8e + iVar1));
    if (sVar2 == 0) {
      commandArgParser(*(undefined2 *)(&DAT_0097fb8c + iVar1));
    }
    else if (sVar2 == 1) {
      sVar2 = commandArgParser(*(undefined2 *)(&DAT_0097fb8c + iVar1));
      FUN_00467910((iVar4 << 0xe) / (int)sVar2);
    }
    else if (sVar2 == 2) {
      sVar2 = commandArgParser(*(undefined2 *)(&DAT_0097fb8c + iVar1));
      FUN_00467910((iVar4 << 0xe) / (int)sVar2);
    }
    commandArgParser(*(undefined2 *)(&DAT_0097fb88 + iVar1));
    commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar1));
    commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar1));
    uVar3 = FUN_004b9d10();
    FUN_0044f060(*(undefined2 *)(&DAT_0097fb84 + iVar1),uVar3);
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
    return 1;
  }
  return 0;
}
```

## Command 0x18
### Official name: msg_disp2
### My guess: Shows a message inside the message box

### Code
```cpp
undefined4 command_0x18_message(int *param_1,undefined4 param_2,int *param_3,int *commandOffsetPtr)
{
  uint *puVar1;
  char cVar2;
  int iVar3;
  undefined4 uVar4;
  int commandOffset;
  
  commandOffset = *commandOffsetPtr;
  if (*param_1 == 0) {
    FUN_0044c700();
    *param_3 = 0;
    *(undefined *)(param_3 + 1) = 0;
    puVar1 = DAT_0095d4d8;
    *(undefined2 *)(DAT_0095d4d8 + 1) = 0;
    if (DAT_0095f6d0 == '\x02') {
      *(undefined2 *)(puVar1 + 1) = 1;
      if (((-1 < *(short *)(&DAT_0097fb88 + commandOffset)) &&
          (cVar2 = FUN_0044b000(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                                *(short *)(&DAT_0097fb88 + commandOffset)), cVar2 == '\0')) &&
         ((DAT_042b52d6 == '\0' || (DAT_042b52d6 == '\x02')))) {
        FUN_0040f5e0(0xf,0);
        *(undefined2 *)(puVar1 + 1) = 0;
        if (DAT_042b52d7 != '\0') {
          *(undefined *)(param_3 + 1) = 1;
        }
        if (DAT_042b52ea != '\0') {
          *(undefined *)(param_3 + 1) = 1;
          FUN_004372f0();
        }
        if (DAT_042b52d6 == '\0') {
          DAT_0095f6d0 = DAT_042b52d6;
        }
        else if (DAT_042b52d6 == '\x02') {
          DAT_0095f6d0 = '\x01';
        }
      }
    }
    else if ((DAT_0095f6d0 == '\x01') && (DAT_0095f6d1 != '\0')) {
      *(undefined2 *)(puVar1 + 1) = 0;
      if ((-1 < *(short *)(&DAT_0097fb88 + commandOffset)) &&
         (cVar2 = FUN_0044b000(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                               *(short *)(&DAT_0097fb88 + commandOffset)), cVar2 != '\0')) {
        FUN_0040f5e0(0xe,0);
        *(undefined2 *)(puVar1 + 1) = 1;
        if (DAT_042b52d7 != '\0') {
          *(undefined *)(param_3 + 1) = 1;
        }
        DAT_0095f6d0 = '\x02';
      }
    }
    if (*(char *)(param_3 + 1) != '\0') {
      return 1;
    }
    if ((((DAT_008e12ac & 0x800) != 0) &&
        (cVar2 = FUN_0044b000(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                              *(undefined2 *)(&DAT_0097fb88 + commandOffset)), cVar2 != '\0')) ||
       ((DAT_008e12ac & 0x200) != 0)) {
      *(undefined2 *)(puVar1 + 1) = 1;
    }
    *puVar1 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[commandOffset];
    *(undefined *)((int)puVar1 + 6) = 1;
    puVar1[2] = (int)*(short *)(&DAT_0097fb88 + commandOffset);
    *(undefined2 *)(puVar1 + 3) = *(undefined2 *)(&DAT_0097fb84 + commandOffset);
    *(undefined2 *)((int)puVar1 + 0xe) = *(undefined2 *)(&DAT_0097fb82 + commandOffset);
    FUN_00450b60(&DAT_008ed600,
                 &scriptBeginAddress_0x97fb80 + *(ushort *)(&DAT_0097fb86 + commandOffset),
                 (byte)(&scriptCommandLength_0x0097fb81)[commandOffset] - 0xe >> 1,
                 &DAT_0097fb8e + commandOffset);
    puVar1[4] = (uint)&DAT_008ed600;
    puVar1[5] = *(uint *)(&DAT_0097fb8a + commandOffset);
    FUN_0047f1e0(DAT_0095d540,0);
    *param_1 = *param_1 + 1;
  }
  else if ((*param_1 == 1) && (iVar3 = FUN_0047f640(DAT_0095d540,1), iVar3 != 0)) {
    if (DAT_0095f6d0 == '\x03') {
      FUN_0044a2c0(0);
      return 1;
    }
    if ((DAT_0095f6d0 != '\0') &&
       (((DAT_008e12ac & 0xd001) != 0 || (iVar3 = FUN_00481bf0(), iVar3 != 0)))) {
      if (DAT_0095f6d0 == '\x01') {
        uVar4 = 0xd;
      }
      else {
        uVar4 = 0xf;
      }
      FUN_0040f5e0(uVar4,0);
      FUN_0044a2c0(0);
    }
    FUN_0044af50(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                 *(undefined2 *)(&DAT_0097fb88 + commandOffset));
    if (*(short *)(&DAT_0097fb88 + commandOffset) < 0) {
      FUN_00442af0();
    }
    *commandOffsetPtr =
         *commandOffsetPtr + (uint)(byte)(&scriptCommandLength_0x0097fb81)[commandOffset];
    return 1;
  }
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x1A
### Official name: window
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x1A_window(int *param_1,undefined4 param_2,int *param_3,int *param_4)

{
  int iVar1;
  uint *puVar2;
  undefined uVar3;
  int iVar4;
  uint uVar5;
  
  iVar1 = *param_4;
  if (*param_1 == 0) {
    *param_3 = 0;
    puVar2 = DAT_0095d4d8;
    *DAT_0095d4d8 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar1];
    *(undefined2 *)(puVar2 + 1) = 0;
    uVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar1));
    *(undefined *)(puVar2 + 0x12) = uVar3;
    uVar5 = FUN_0047ebc0();
    puVar2[0x13] = uVar5;
    FUN_0047f1e0(DAT_0095d540,0);
    *param_1 = *param_1 + 1;
  }
  else if (*param_1 == 1) {
    iVar4 = FUN_0047f640(DAT_0095d540,1);
    if (iVar4 != 0) {
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
      return 1;
    }
  }
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x1C
### Official name: selectP
### My guess: (N/A)

### Code
```cpp
void command_0x1C_selectP(uint *param_1,undefined4 param_2,int *param_3,int *param_4)
{
  undefined4 *puVar1;
  uint *puVar2;
  undefined uVar3;
  short sVar4;
  undefined2 uVar5;
  int iVar6;
  int iVar7;
  int iVar8;
  uint uVar9;
  uint *local_40c;
  int *local_408;
  char local_404 [1024];
  uint local_4;
  
  puVar1 = DAT_0095d4d8;
  local_4 = DAT_004f7b40 ^ (uint)&local_40c;
  iVar7 = *param_4;
  local_40c = param_1;
  local_408 = param_4;
  switch(*param_1) {
  case 0:
    *param_3 = 0;
    puVar2 = DAT_0095d4e8;
    *DAT_0095d4e8 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar7];
    *(undefined2 *)(puVar2 + 2) = *(undefined2 *)(&DAT_0097fb84 + iVar7);
    *(undefined2 *)((int)puVar2 + 10) = *(undefined2 *)(&DAT_0097fb86 + iVar7);
    *(undefined2 *)(puVar2 + 3) = 0xffff;
    *(undefined2 *)((int)puVar2 + 0xe) = 0;
    sVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb88 + iVar7));
    param_3[2] = (int)(&scriptBeginAddress_0x97fb80 + sVar4);
    param_3[3] = 0;
    sVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar7));
    if (sVar4 == 0) {
      local_408 = (int *)0x0;
      if (*(short *)param_3[2] != 0) {
        iVar6 = 0;
        do {
          sVar4 = commandArgParser(*(undefined2 *)(param_3[2] + 2 + iVar6));
          if (sVar4 != 0) {
            puVar2[param_3[3] * 3 + 4] =
                 (uint)(&scriptBeginAddress_0x97fb80 + *(ushort *)(param_3[2] + iVar6));
            *(undefined2 *)(puVar2 + param_3[3] * 3 + 5) = local_408._0_2_;
            *(undefined2 *)((int)puVar2 + param_3[3] * 0xc + 0x16) =
                 *(undefined2 *)(param_3[2] + 4 + iVar6);
            *(undefined *)(puVar2 + (param_3[3] + 2) * 3) = *(undefined *)(param_3[2] + 7 + iVar6);
            *(undefined *)((int)puVar2 + param_3[3] * 0xc + 0x19) =
                 *(undefined *)(param_3[2] + 7 + iVar6);
            param_3[3] = param_3[3] + 1;
          }
          local_408 = (int *)((int)local_408 + 1);
          iVar6 = (int)local_408 * 8;
          param_1 = local_40c;
        } while (*(short *)(param_3[2] + (int)local_408 * 8) != 0);
      }
    }
    else {
      iVar6 = 0;
      sVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar7));
      param_1 = local_40c;
      if (0 < sVar4) {
        do {
          sVar4 = commandArgParser(*(undefined2 *)(param_3[2] + 2 + iVar6 * 8));
          if (sVar4 != 0) {
            puVar2[param_3[3] * 3 + 4] =
                 (uint)(&scriptBeginAddress_0x97fb80 + *(ushort *)(param_3[2] + iVar6 * 8));
            *(short *)(puVar2 + param_3[3] * 3 + 5) = (short)iVar6;
            *(undefined2 *)((int)puVar2 + param_3[3] * 0xc + 0x16) =
                 *(undefined2 *)(param_3[2] + 4 + iVar6 * 8);
            *(undefined *)(puVar2 + (param_3[3] + 2) * 3) =
                 *(undefined *)(param_3[2] + 7 + iVar6 * 8);
            *(undefined *)((int)puVar2 + param_3[3] * 0xc + 0x19) =
                 *(undefined *)(param_3[2] + 7 + iVar6 * 8);
            param_3[3] = param_3[3] + 1;
          }
          iVar6 = iVar6 + 1;
          sVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar7));
          param_1 = local_40c;
        } while (iVar6 < sVar4);
      }
    }
    iVar6 = param_3[3];
    if (iVar6 == 0) {
      param_3[1] = 0;
      uVar9 = 0xffffffff;
    }
    else {
      if (iVar6 != 1) {
        *(short *)((int)puVar2 + 6) = (short)iVar6;
        *(undefined2 *)(puVar2 + 1) = 0;
        if (DAT_0095f6d0 == '\x02') {
          *(undefined2 *)(puVar2 + 1) = 1;
        }
        FUN_0047e920(DAT_0095d550,&LAB_0043ddb0,"task select_call");
        goto LAB_00451d39;
      }
      param_3[1] = 0;
      uVar9 = (uint)*(ushort *)(puVar2 + 5);
    }
    FUN_0044f060(*(undefined2 *)(&DAT_0097fb84 + iVar7),uVar9);
    *param_1 = (-(uint)(((&DAT_0097fb86)[iVar7] & 2) != 0) & 0xfffffffe) + 4;
    break;
  case 1:
    iVar6 = FUN_0047eb90(DAT_0095d550);
    if (iVar6 != 0) {
      iVar6 = FUN_0047eaa0(DAT_0095d550);
      param_3[1] = iVar6;
      if ((((&DAT_0097fb86)[iVar7] & 2) != 0) && (iVar6 == 0)) goto LAB_00451d39;
      *param_1 = 4;
    }
    break;
  case 2:
    *(undefined2 *)(DAT_0095d4d8 + 1) = 1;
    *puVar1 = 0x18;
    *(undefined *)((int)puVar1 + 6) = 1;
    puVar1[2] = 0xffffffff;
    *(undefined2 *)(puVar1 + 3) = 0xffff;
    *(undefined2 *)((int)puVar1 + 0xe) = 0;
    puVar1[4] = &DAT_004e1000;
    puVar1[5] = 0;
    FUN_0047f1e0(DAT_0095d540,0);
LAB_00451d39:
    *param_1 = *param_1 + 1;
    break;
  case 3:
    iVar7 = FUN_0047f640(DAT_0095d540,1);
    if (iVar7 != 0) goto LAB_00451d39;
    break;
  case 4:
    switch(param_3[1]) {
    case 0:
      iVar6 = 0;
      if (param_3[3] == 0) {
        *param_4 = (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar7] + iVar7;
      }
      else {
        sVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar7));
        iVar8 = (int)sVar4;
        local_40c = (uint *)0x0;
        if (0 < iVar8) {
          do {
            sVar4 = commandArgParser(*(undefined2 *)(param_3[2] + 2 + iVar6 * 8));
            if (sVar4 != 0) {
              local_40c = (uint *)((int)local_40c + 1);
            }
            iVar6 = iVar6 + 1;
          } while (iVar6 < iVar8);
        }
        uVar3 = FUN_0044b150(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                             *(undefined2 *)(param_3[2] + 4 + iVar8 * 8));
        FUN_0044b0b0(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                     *(undefined2 *)(param_3[2] + 4 + iVar8 * 8));
        if ((1 < param_3[3]) ||
           (sVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar7)), sVar4 == 1)) {
          if ((((&DAT_0097fb86)[iVar7] & 4) == 0) ||
             (sVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar7)), iVar8 != sVar4 + -1)
             ) {
            FUN_00440c50();
            _sprintf(local_404,&DAT_004e0ff8,
                     &scriptBeginAddress_0x97fb80 + *(ushort *)(param_3[2] + iVar8 * 8));
            FUN_00442eb0(uVar3,local_404);
          }
          FUN_00440c50();
          if (((((&DAT_0097fb86)[iVar7] & 1) != 0) && ((DAT_042b52dd & 1) != 0)) &&
             ((DAT_0095f6c6 & 8) == 0)) {
            DAT_0095f6d3 = local_40c._0_1_;
            DAT_0095f6c9 = 1;
            uVar5 = FUN_0044b1f0(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                                 *(undefined2 *)(param_3[2] + 4 + iVar8 * 8));
            FUN_0044c600(2,uVar5);
            DAT_0095f6d3 = 0xff;
          }
        }
        *local_408 = *local_408 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar7];
      }
      break;
    case 1:
    case 2:
    case 3:
      FUN_0047ea60(0xffffffff,param_3[1]);
      break;
    case 4:
      break;
    default:
      goto switchD_00451e06_caseD_5;
    }
    goto LAB_00451d42;
  }
switchD_00451e06_caseD_5:
  *param_3 = *param_3 + 1;
LAB_00451d42:
  FUN_004b9e36();
  return;
}
```

## Command 0x1D
### Official name: select2
### My guess: (N/A)

### Code
```cpp

undefined4 command_0x1D_select2(int *param_1,undefined4 param_2,int *param_3,uint *param_4)

{
  short **ppsVar1;
  ushort uVar2;
  uint uVar3;
  undefined4 *puVar4;
  uint *puVar5;
  int *piVar6;
  char cVar7;
  undefined uVar8;
  short sVar9;
  undefined2 uVar10;
  int iVar11;
  uint *puVar12;
  int iVar13;
  int local_c;
  uint *local_8;
  
  piVar6 = param_3;
  puVar4 = DAT_0095d4d8;
  uVar3 = *param_4;
  switch(*param_1) {
  case 0:
    *param_3 = 0;
    puVar5 = DAT_0095d4e8;
    *DAT_0095d4e8 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[uVar3];
    *(undefined2 *)(puVar5 + 2) = *(undefined2 *)(&DAT_0097fb84 + uVar3);
    *(undefined2 *)((int)puVar5 + 10) = *(undefined2 *)(&DAT_0097fb86 + uVar3);
    *(undefined2 *)(puVar5 + 3) = 0xffff;
    *(undefined2 *)((int)puVar5 + 0xe) = 0;
    param_3[2] = (int)(&DAT_0097fb88 + uVar3);
    local_c = 0;
    sVar9 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + uVar3));
    if (sVar9 == 0) {
      ppsVar1 = (short **)(param_3 + 2);
      param_3 = (int *)0x0;
      if (**ppsVar1 == 0) goto LAB_004521a0;
      iVar11 = 0;
      puVar12 = puVar5 + 5;
      do {
        sVar9 = commandArgParser(*(undefined2 *)(iVar11 + 4 + piVar6[2]));
        if (sVar9 != 0) {
          local_c = local_c + 1;
          puVar12[-1] = (uint)(&scriptBeginAddress_0x97fb80 + *(ushort *)(iVar11 + piVar6[2]));
          *(short *)puVar12 = (short)param_3;
          *(undefined2 *)((int)puVar12 + 2) = *(undefined2 *)(iVar11 + 6 + piVar6[2]);
          *(undefined *)(puVar12 + 1) = *(undefined *)(iVar11 + 9 + piVar6[2]);
          *(undefined *)((int)puVar12 + 5) = *(undefined *)(iVar11 + 9 + piVar6[2]);
          puVar12 = puVar12 + 3;
        }
        param_3 = (int *)((int)param_3 + 1);
        iVar11 = (int)param_3 * 10;
      } while (*(short *)(iVar11 + piVar6[2]) != 0);
    }
    else {
      iVar11 = 0;
      param_3 = (int *)0x0;
      sVar9 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + uVar3));
      if (sVar9 < 1) goto LAB_004521a0;
      puVar12 = puVar5 + 5;
      do {
        sVar9 = commandArgParser(*(undefined2 *)(piVar6[2] + 4 + iVar11));
        if (sVar9 != 0) {
          uVar2 = *(ushort *)(piVar6[2] + iVar11);
          local_c = local_c + 1;
          *(undefined2 *)puVar12 = param_3._0_2_;
          puVar12[-1] = (uint)(&scriptBeginAddress_0x97fb80 + uVar2);
          *(undefined2 *)((int)puVar12 + 2) = *(undefined2 *)(piVar6[2] + 6 + iVar11);
          *(undefined *)(puVar12 + 1) = *(undefined *)(piVar6[2] + 9 + iVar11);
          *(undefined *)((int)puVar12 + 5) = *(undefined *)(piVar6[2] + 9 + iVar11);
          puVar12 = puVar12 + 3;
        }
        param_3 = (int *)((int)param_3 + 1);
        iVar11 = iVar11 + 10;
        sVar9 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + uVar3));
      } while ((int)param_3 < (int)sVar9);
    }
    local_8 = puVar5 + 5;
    if (local_c == 0) {
LAB_004521a0:
      FUN_0044f060(*(undefined2 *)(&DAT_0097fb84 + uVar3),0xffffffff);
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[uVar3];
      return 1;
    }
    if (local_c != 1) {
      *(short *)((int)puVar5 + 6) = (short)local_c;
      *(undefined2 *)(puVar5 + 1) = 0;
      if (DAT_0095f6d0 == '\x02') {
        *(undefined2 *)(puVar5 + 1) = 1;
      }
      FUN_0047e920(DAT_0095d550,&LAB_0043ddb0,"task select_call");
      *param_1 = *param_1 + 1;
      *piVar6 = *piVar6 + 1;
      return 0;
    }
    uVar10 = *(undefined2 *)(&DAT_0097fb84 + uVar3);
    FUN_0044f060(uVar10,*(undefined2 *)local_8);
    sVar9 = commandArgParser(uVar10);
    goto LAB_004521e2;
  case 1:
    iVar11 = FUN_0047eb90(DAT_0095d550);
    if (iVar11 == 0) goto switchD_00452007_caseD_5;
    iVar11 = FUN_0047eaa0(DAT_0095d550);
    param_3[1] = iVar11;
    if ((((&DAT_0097fb86)[uVar3] & 2) == 0) || (iVar11 != 0)) {
      *param_1 = 4;
      *param_3 = *param_3 + 1;
      return 0;
    }
    break;
  case 2:
    *(undefined2 *)(DAT_0095d4d8 + 1) = 1;
    *puVar4 = 0x18;
    *(undefined *)((int)puVar4 + 6) = 1;
    puVar4[2] = 0xffffffff;
    *(undefined2 *)(puVar4 + 3) = 0xffff;
    *(undefined2 *)((int)puVar4 + 0xe) = 0;
    puVar4[4] = &DAT_004e1000;
    puVar4[5] = 0;
    FUN_0047f1e0(DAT_0095d540,0);
    break;
  case 3:
    iVar11 = FUN_0047f640(DAT_0095d540,1);
    if (iVar11 != 0) {
      *param_1 = *param_1 + 1;
      *param_3 = *param_3 + 1;
      return 0;
    }
    goto switchD_00452007_caseD_5;
  case 4:
    switch(param_3[1]) {
    case 0:
      sVar9 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + uVar3));
      iVar11 = (int)sVar9;
      iVar13 = 0;
      param_1._0_1_ = '\0';
      param_3 = (int *)iVar11;
      cVar7 = '\0';
      if (0 < iVar11) {
        do {
          param_1._0_1_ = cVar7;
          sVar9 = commandArgParser(*(undefined2 *)(piVar6[2] + 4 + iVar13));
          if (sVar9 != 0) {
            param_1._0_1_ = (char)param_1 + '\x01';
          }
          iVar13 = iVar13 + 10;
          param_3 = (int *)((int)param_3 + -1);
          cVar7 = (char)param_1;
        } while (param_3 != (int *)0x0);
      }
      iVar11 = iVar11 * 10;
      uVar8 = FUN_0044b150(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                           *(undefined2 *)(iVar11 + 6 + piVar6[2]));
      FUN_00442e30(uVar8,&scriptBeginAddress_0x97fb80 + *(ushort *)(iVar11 + piVar6[2]));
      FUN_0044b0b0(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                   *(undefined2 *)(iVar11 + 6 + piVar6[2]));
      if (((((&DAT_0097fb86)[uVar3] & 1) != 0) && ((DAT_042b52dd & 1) != 0)) &&
         ((DAT_0095f6c6 & 8) == 0)) {
        DAT_0095f6d3 = (char)param_1;
        DAT_0095f6c9 = 1;
        uVar10 = FUN_0044b1f0(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                              *(undefined2 *)(iVar11 + 6 + piVar6[2]));
        FUN_0044c600(2,uVar10);
        DAT_0095f6d3 = 0xff;
      }
      sVar9 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + uVar3));
      break;
    case 1:
    case 2:
    case 3:
      FUN_0047ea60(0xffffffff,param_3[1]);
      return 3;
    case 4:
      return 2;
    default:
      goto switchD_00452007_caseD_5;
    }
LAB_004521e2:
    *param_4 = (uint)*(ushort *)(piVar6[2] + 2 + sVar9 * 10);
    return 1;
  default:
    goto switchD_00452007_caseD_5;
  }
  *param_1 = *param_1 + 1;
switchD_00452007_caseD_5:
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x1F
### Official name: mesSync
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x1F_mesSync(int *param_1,undefined4 param_2,int *param_3,int *param_4)

{
  ushort uVar1;
  int iVar2;
  byte *pbVar3;
  char cVar4;
  int iVar5;
  undefined *puVar6;
  uint uVar7;
  uint *puVar8;
  undefined4 uVar9;
  byte *local_10 [4];
  
  iVar2 = *param_4;
  uVar1 = *(ushort *)(&DAT_0097fb82 + iVar2);
  iVar5 = 0;
  uVar7 = (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
  if (uVar1 != 0) {
    do {
      local_10[iVar5] = &scriptBeginAddress_0x97fb80 + uVar7 + iVar2;
      iVar5 = iVar5 + 1;
      uVar7 = uVar7 + (byte)(&scriptBeginAddress_0x97fb80 + uVar7 + iVar2)[1];
    } while (iVar5 < (int)(uint)uVar1);
  }
  if (*param_1 == 0) {
    *param_3 = 0;
    *(undefined *)(param_3 + 1) = 0;
    puVar8 = DAT_0095d4d8;
    *(undefined2 *)(DAT_0095d4d8 + 1) = 0;
    if (DAT_0095f6d0 == '\x02') {
      *(undefined2 *)(puVar8 + 1) = 1;
      if (((-1 < *(short *)(local_10[0] + 8)) &&
          (cVar4 = FUN_0044b000(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                                *(short *)(local_10[0] + 8)), cVar4 == '\0')) &&
         ((DAT_042b52d6 == '\0' || (DAT_042b52d6 == '\x02')))) {
        FUN_0040f5e0(0xf,0);
        *(undefined2 *)(puVar8 + 1) = 0;
        if (DAT_042b52d7 != '\0') {
          *(undefined *)(param_3 + 1) = 1;
        }
        if (DAT_042b52ea != '\0') {
          *(undefined *)(param_3 + 1) = 1;
          FUN_004372f0();
        }
        if (DAT_042b52d6 == '\0') {
          DAT_0095f6d0 = DAT_042b52d6;
        }
        else if (DAT_042b52d6 == '\x02') {
          DAT_0095f6d0 = '\x01';
        }
      }
    }
    else if ((DAT_0095f6d0 == '\x01') && (DAT_0095f6d1 != '\0')) {
      *(undefined2 *)(puVar8 + 1) = 0;
      if ((-1 < *(short *)(local_10[0] + 8)) &&
         (cVar4 = FUN_0044b000(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                               *(short *)(local_10[0] + 8)), cVar4 != '\0')) {
        FUN_0040f5e0(0xe,0);
        *(undefined2 *)(puVar8 + 1) = 1;
        if (DAT_042b52d7 != '\0') {
          *(undefined *)(param_3 + 1) = 1;
        }
        DAT_0095f6d0 = '\x02';
      }
    }
    if (*(char *)(param_3 + 1) == '\0') {
      if ((((DAT_008e12ac & 0x800) != 0) &&
          (cVar4 = FUN_0044b000(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                                *(undefined2 *)(local_10[0] + 8)), cVar4 != '\0')) ||
         ((DAT_008e12ac & 0x200) != 0)) {
        *(undefined2 *)(puVar8 + 1) = 1;
      }
      *puVar8 = (uint)*local_10[0];
      iVar5 = 0;
      *(undefined *)((int)puVar8 + 6) = (&DAT_0097fb82)[iVar2];
      if (*(short *)(&DAT_0097fb82 + iVar2) != 0) {
        puVar6 = &DAT_008ed600;
        puVar8 = puVar8 + 3;
        do {
          pbVar3 = local_10[iVar5];
          puVar8[-1] = (int)*(short *)(pbVar3 + 8);
          *(undefined2 *)puVar8 = *(undefined2 *)(pbVar3 + 4);
          *(undefined2 *)((int)puVar8 + 2) = *(undefined2 *)(pbVar3 + 2);
          FUN_00450b60(puVar6,&scriptBeginAddress_0x97fb80 + *(ushort *)(pbVar3 + 6),
                       pbVar3[1] - 0xe >> 1,pbVar3 + 0xe);
          puVar8[1] = (uint)puVar6;
          puVar8[2] = *(uint *)(pbVar3 + 10);
          iVar5 = iVar5 + 1;
          puVar6 = puVar6 + 0x800;
          puVar8 = puVar8 + 4;
        } while (iVar5 < (int)(uint)*(ushort *)(&DAT_0097fb82 + iVar2));
      }
      FUN_0047f1e0(DAT_0095d540,0);
      *param_1 = *param_1 + 1;
      *param_3 = *param_3 + 1;
      return 0;
    }
  }
  else {
    if ((*param_1 != 1) || (iVar5 = FUN_0047f640(DAT_0095d540,1), iVar5 == 0)) {
      *param_3 = *param_3 + 1;
      return 0;
    }
    if (DAT_0095f6d0 != '\x03') {
      if ((DAT_0095f6d0 != '\0') &&
         (((DAT_008e12ac & 0xd001) != 0 || (iVar5 = FUN_00481bf0(), iVar5 != 0)))) {
        if (DAT_0095f6d0 == '\x01') {
          uVar9 = 0xd;
        }
        else {
          uVar9 = 0xf;
        }
        FUN_0040f5e0(uVar9,0);
        FUN_0044a2c0(0);
      }
      iVar5 = 0;
      if (*(short *)(&DAT_0097fb82 + iVar2) != 0) {
        do {
          FUN_0044af50(sceneNumber_0x95f4a0,scriptNameIndex_95f4a4,
                       *(undefined2 *)(local_10[iVar5] + 8));
          iVar5 = iVar5 + 1;
        } while (iVar5 < (int)(uint)*(ushort *)(&DAT_0097fb82 + iVar2));
      }
      if (*(short *)(local_10[0] + 8) < 0) {
        FUN_00442af0();
      }
      *param_4 = *param_4 + uVar7;
      return 1;
    }
    FUN_0044a2c0(0);
  }
  return 1;
}
```
## Command 0x20
### Official name: screenMode
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x20_screenMode(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)

{
  int iVar1;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  DAT_0095f6cb = (&DAT_0097fb82)[iVar1];
  DAT_0095f6cc = (&DAT_0097fb84)[iVar1];
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x21
### Official name: setSavePoint
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x21_setSavePoint(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)

{
  int iVar1;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  FUN_00436030();
  FUN_0044c700();
  FUN_0044ae80();
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  DAT_0095f6ca = 1;
  FUN_0044aea0();
  return 1;
}
```

## Command 0x22
### Official name: clearSavePoint
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x22_clearSavePoint(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)

{
  if (*param_1 != 0) {
    return 0;
  }
  DAT_0095f6ca = 0;
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[*param_4];
  return 1;
}

```

## Command 0x23
### Official name: setPrevoiusPoint
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x22_clearSavePoint(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  if (*param_1 != 0) {
    return 0;
  }
  DAT_0095f6ca = 0;
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[*param_4];
  return 1;
}
```

## Command 0x24
### Official name: mesLog
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x24_mesLog(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)

{
  int iVar1;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  if (*(ushort *)(&DAT_0097fb82 + iVar1) == 0) {
    FUN_004432a0(0xffffffff);
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
    return 1;
  }
  FUN_00442eb0(0,&scriptBeginAddress_0x97fb80 + *(ushort *)(&DAT_0097fb82 + iVar1));
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x25
### Official name: autoStart
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x25_autoStart(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  int iVar1;
  undefined4 uVar2;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  FUN_00436030();
  if (DAT_042b52d9 == '\0') {
    uVar2 = 0;
  }
  else if (DAT_042b52d9 == '\x01') {
    uVar2 = 1;
  }
  else {
    if (DAT_042b52d9 != '\x02') goto LAB_00452819;
    uVar2 = 2;
  }
  FUN_0044a2c0(uVar2);
LAB_00452819:
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x26
### Official name: autoStop
### My guess: (N/A)

### Code
```cpp

undefined4 command_0x26_autoStop(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  int iVar1;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  FUN_00436030();
  FUN_0044a2c0(0);
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x27
### Official name: quickSave
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x27_quickSave(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  ushort uVar1;
  int iVar2;
  short sVar3;
  undefined4 uVar4;
  
  iVar2 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  FUN_00436030();
  uVar1 = *(ushort *)(&DAT_0097fb82 + iVar2);
  if (((uVar1 == 0) || ((DAT_042b52dd & (byte)uVar1) != 0)) && ((DAT_0095f6c6 & 8) == 0)) {
    DAT_0095f6c9 = 1;
    if ((uVar1 & 2) == 0) {
      if ((uVar1 & 1) == 0) goto LAB_004528e4;
      sVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
      uVar4 = 2;
    }
    else {
      sVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
      uVar4 = 1;
    }
    FUN_0044c600(uVar4,(int)sVar3);
  }
LAB_004528e4:
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
  return 1;
}
```

## Command 0x28
### Official name: titleDisplay
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x28_titleDisplay(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  int iVar1;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  if ((&DAT_0097fb82)[iVar1] == '\0') {
    DAT_0095f4a6 = FUN_00452940(scriptNameIndex_95f4a4);
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
    return 1;
  }
  DAT_0095f4a6 = 0xffff;
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x29
### Official name: dateDisplay
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x29_dateDisplay(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  int iVar1;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  if ((&DAT_0097fb82)[iVar1] == '\0') {
    DAT_0095f4aa = 1;
    DAT_0095f4ac = 1;
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
    return 1;
  }
  DAT_0095f4aa = 0;
  DAT_0095f4ac = 0;
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x2B
### Official name: locationDisplay
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x2B_locationDisplay(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)

{
  if (*param_1 != 0) {
    return 0;
  }
  DAT_0095f4a8 = (ushort)((&DAT_0097fb82)[*param_4] == '\0');
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[*param_4];
  return 1;
}
```

## Command 0x02C
### Official name: getOptions
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x2C_getOptions(int *param_1,undefined4 param_2,int *param_3,int *param_4)
{
  int iVar1;
  short sVar2;
  undefined4 uVar3;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    *param_3 = *param_3 + 1;
    return 0;
  }
  sVar2 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar1));
  uVar3 = FUN_00444830((int)sVar2);
  FUN_0044f060(*(undefined2 *)(&DAT_0097fb84 + iVar1),uVar3);
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x2D
### Official name: setIcon
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x2D_setIcon(int *param_1,undefined4 param_2,int *param_3,int *param_4)
{
  int iVar1;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    *param_3 = *param_3 + 1;
    return 0;
  }
  DAT_0095f4a3 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar1));
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x2E
### Official name: menuEnable
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x2E_menuEnable(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)

{
  if (*param_1 != 0) {
    return 0;
  }
  _DAT_0095f6c6 = _DAT_0095f6c6 & ~*(ushort *)(&DAT_0097fb82 + *param_4);
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[*param_4];
  return 1;
}
```

## Command 0x02F
### Official name: menuDisable
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x2F_menuDisable(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  if (*param_1 != 0) {
    return 0;
  }
  _DAT_0095f6c6 = _DAT_0095f6c6 | *(ushort *)(&DAT_0097fb82 + *param_4);
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[*param_4];
  return 1;
}
```

## Command 0x30
### Official name: fadeOut
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x30_fadeOut(int *param_1,undefined4 param_2,int *param_3,int *param_4)
{
  int iVar1;
  uint *puVar2;
  undefined2 uVar3;
  int iVar4;
  
  iVar1 = *param_4;
  if (*param_1 == 0) {
    *param_3 = 0;
    uVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar1));
    *(undefined2 *)(param_3 + 1) = uVar3;
    puVar2 = DAT_0095d4d4;
    *DAT_0095d4d4 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar1];
    uVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar1));
    *(undefined2 *)(puVar2 + 4) = uVar3;
    uVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar1));
    *(undefined2 *)((int)puVar2 + 0xe) = uVar3;
    *(undefined2 *)(puVar2 + 3) = *(undefined2 *)(&DAT_0097fb86 + iVar1);
    *(undefined2 *)((int)puVar2 + 10) = 0;
    if ((DAT_0095f6d0 == '\x02') || ((DAT_008e12ac & 0xa00) != 0)) {
      *(undefined2 *)((int)puVar2 + 10) = 1;
    }
    FUN_0047f1e0(DAT_0095d53c,0);
    *param_1 = *param_1 + 1;
  }
  else if (*param_1 == 1) {
    iVar4 = FUN_0047f640(DAT_0095d514,1);
    if (iVar4 != 0) {
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
      return 2;
    }
  }
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x31 0x33
### Official name: fadeOutStop
### My guess: (N/A)

### Code
```cpp
undefined4
command_0x31_0x33_fadeIn_fadeOutStop(int *param_1,undefined4 param_2,int *param_3,int *param_4)

{
  int iVar1;
  uint *puVar2;
  undefined2 uVar3;
  int iVar4;
  
  iVar1 = *param_4;
  if (*param_1 == 0) {
    *param_3 = 0;
    puVar2 = DAT_0095d4d4;
    *DAT_0095d4d4 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar1];
    uVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar1));
    *(undefined2 *)(puVar2 + 4) = uVar3;
    uVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar1));
    *(undefined2 *)((int)puVar2 + 0xe) = uVar3;
    *(undefined2 *)((int)puVar2 + 10) = 0;
    if ((DAT_0095f6d0 == '\x02') || ((DAT_008e12ac & 0xa00) != 0)) {
      *(undefined2 *)((int)puVar2 + 10) = 1;
    }
    FUN_0047f1e0(DAT_0095d53c,0);
    *param_1 = *param_1 + 1;
  }
  else if (*param_1 == 1) {
    iVar4 = FUN_0047f640(DAT_0095d514,1);
    if (iVar4 != 0) {
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
      return 2;
    }
  }
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x32
### Official name: fadeOutStart
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x32_fadeOutStart(int *param_1,undefined4 param_2,int *param_3,int *param_4)
{
  int iVar1;
  uint *puVar2;
  undefined2 uVar3;
  int iVar4;
  
  iVar1 = *param_4;
  if (*param_1 == 0) {
    *param_3 = 0;
    *(undefined2 *)(param_3 + 1) = *(undefined2 *)(&DAT_0097fb86 + iVar1);
    puVar2 = DAT_0095d4d4;
    *DAT_0095d4d4 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar1];
    uVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar1));
    *(undefined2 *)(puVar2 + 4) = uVar3;
    uVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar1));
    *(undefined2 *)((int)puVar2 + 0xe) = uVar3;
    *(undefined2 *)(puVar2 + 3) = *(undefined2 *)(&DAT_0097fb86 + iVar1);
    *(undefined2 *)((int)puVar2 + 10) = 0;
    if ((DAT_0095f6d0 == '\x02') || ((DAT_008e12ac & 0xa00) != 0)) {
      *(undefined2 *)((int)puVar2 + 10) = 1;
    }
    FUN_0047f1e0(DAT_0095d53c,0);
    *param_1 = *param_1 + 1;
  }
  else if (*param_1 == 1) {
    iVar4 = FUN_0047f640(DAT_0095d514,1);
    if (iVar4 != 0) {
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
      return 2;
    }
  }
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x33
### Official name: charErase
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x33_charErase(int *param_1,undefined4 param_2,int *param_3,int *param_4)
{
  int iVar1;
  int iVar2;
  uint *puVar3;
  undefined uVar4;
  short sVar5;
  int iVar6;
  uint uVar7;
  undefined2 extraout_var;
  undefined2 extraout_var_00;
  undefined2 *puVar8;
  uint *puVar9;
  uint uVar10;
  
  iVar2 = *param_4;
  if (*param_1 == 0) {
    *param_3 = 0;
    sVar5 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar2));
    if (sVar5 == 0x4000) {
      uVar10 = 6;
      iVar6 = 0;
      do {
        *(char *)(iVar6 + 4 + (int)param_3) = (char)iVar6;
        iVar6 = iVar6 + 1;
      } while (iVar6 < 6);
    }
    else {
      uVar10 = (uint)(byte)(&DAT_0097fb82)[iVar2];
      iVar6 = 0;
      if (uVar10 != 0) {
        puVar8 = (undefined2 *)(&DAT_0097fb86 + iVar2);
        do {
          uVar4 = commandArgParser(*puVar8);
          *(undefined *)((int)param_3 + iVar6 + 4) = uVar4;
          iVar6 = iVar6 + 1;
          puVar8 = puVar8 + 1;
        } while (iVar6 < (int)uVar10);
      }
    }
    iVar6 = 0;
    if (uVar10 != 0) {
      do {
        iVar1 = iVar6 + 4;
        iVar6 = iVar6 + 1;
        (&DAT_0095f72c)[*(char *)(iVar1 + (int)param_3) * 0xe] = 0xffff;
      } while (iVar6 < (int)uVar10);
    }
    puVar3 = DAT_0095d4d4;
    uVar7 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar2];
    iVar6 = 0;
    *DAT_0095d4d4 = uVar7;
    *(undefined2 *)((int)puVar3 + 10) = 0;
    if ((DAT_0095f6d0 == '\x02') || ((DAT_008e12ac & 0xa00) != 0)) {
      *(undefined2 *)((int)puVar3 + 10) = 1;
    }
    *(short *)(puVar3 + 2) = (short)uVar10;
    if ((short)uVar10 != 0) {
      puVar9 = puVar3 + 8;
      do {
        *(short *)(puVar9 + -5) = (short)*(char *)((int)param_3 + iVar6 + 4);
        uVar10 = commandArgParser(uVar7 & 0xffff0000 |
                                  (uint)(ushort)(short)(char)(&DAT_0097fb83)[iVar2]);
        if (((short)uVar10 == 0) ||
           (uVar10 = commandArgParser(CONCAT22(extraout_var,(short)(char)(&DAT_0097fb83)[iVar2])),
           (short)uVar10 == 3)) {
          *(undefined *)puVar9 = 2;
        }
        else {
          uVar10 = commandArgParser(CONCAT22(extraout_var_00,(short)(char)(&DAT_0097fb83)[iVar2]));
          *(char *)puVar9 = (char)uVar10;
        }
        uVar7 = commandArgParser(uVar10 & 0xffff0000 | (uint)(byte)(&DAT_0097fb84)[iVar2]);
        *(char *)((int)puVar9 + 1) = (char)uVar7;
        iVar6 = iVar6 + 1;
        puVar9 = (uint *)((int)puVar9 + 0x16);
      } while (iVar6 < (int)(uint)*(ushort *)(puVar3 + 2));
    }
    FUN_0047f1e0(DAT_0095d53c,0);
    *param_1 = *param_1 + 1;
  }
  else if ((*param_1 == 1) && (iVar6 = FUN_0047f640(DAT_0095d538,1), iVar6 != 0)) {
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 2;
  }
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x34
### Official name: fadeWait
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x34_fadeWait(int *param_1,undefined4 param_2,int *param_3,int *param_4)

{
  int iVar1;
  uint *puVar2;
  int iVar3;
  
  iVar1 = *param_4;
  if (*param_1 == 0) {
    *param_3 = 0;
    puVar2 = DAT_0095d4d4;
    *DAT_0095d4d4 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar1];
    *(undefined2 *)((int)puVar2 + 10) = 0;
    if ((DAT_0095f6d0 == '\x02') || ((DAT_008e12ac & 0xa00) != 0)) {
      *(undefined2 *)((int)puVar2 + 10) = 1;
    }
    FUN_0047f1e0(DAT_0095d53c,0);
    *param_1 = *param_1 + 1;
  }
  else if (*param_1 == 1) {
    iVar3 = FUN_0047f640(DAT_0095d514,1);
    if (iVar3 != 0) {
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
      return 2;
    }
  }
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x036
### Official name: fadePri
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x36_fadePri(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  if (*param_1 != 0) {
    return 0;
  }
  *param_4 = (uint)(byte)(&scriptCommandLength_0x0097fb81)[*param_4] + *param_4;
  return 1;
}
```

## Command 0x38
### Official name: filtIn
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x38_filtIn(void)

{
  int in_EAX;
  int iVar1;
  int *unaff_EBP;
  int unaff_ESI;
  int *unaff_EDI;
  
  if (in_EAX == 1) {
    iVar1 = FUN_0047eb90((&DAT_0095d520)[*(ushort *)(unaff_ESI + 2)]);
    if (iVar1 != 0) {
      *unaff_EDI = *unaff_EDI + (uint)*(byte *)(unaff_ESI + 1);
      return 2;
    }
  }
  *unaff_EBP = *unaff_EBP + 1;
  return 0;
}
```

## Command 0x39
### Official name: filtOut
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x39_filtOut(int *param_1,undefined4 param_2,int *param_3,int *param_4)
{
  int iVar1;
  uint *puVar2;
  int iVar3;
  
  iVar1 = *param_4;
  if (*param_1 == 0) {
    *param_3 = 0;
    puVar2 = DAT_0095d4d4;
    DAT_0095f9c0 = 0xffff;
    DAT_0095f9c2 = 0;
    *DAT_0095d4d4 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar1];
    *(undefined2 *)(puVar2 + 4) = *(undefined2 *)(&DAT_0097fb82 + iVar1);
    *(undefined2 *)((int)puVar2 + 10) = 0;
    if ((DAT_0095f6d0 == '\x02') || ((DAT_008e12ac & 0xa00) != 0)) {
      *(undefined2 *)((int)puVar2 + 10) = 1;
    }
    FUN_0047f1e0(DAT_0095d53c,0);
    *param_1 = *param_1 + 1;
  }
  else if (*param_1 == 1) {
    iVar3 = FUN_0047f640(DAT_0095d518,1);
    if (iVar3 != 0) {
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
      return 2;
    }
  }
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x3A
### Official name: filtInStart
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x3A_filtInStart(int *param_1,undefined4 param_2,int *param_3,int *param_4)
{
  int iVar1;
  uint *puVar2;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    *param_3 = *param_3 + 1;
    return 0;
  }
  *param_3 = 0;
  puVar2 = DAT_0095d4d4;
  DAT_0095f9c0 = *(undefined2 *)(&DAT_0097fb84 + iVar1);
  DAT_0095f9c2 = *(undefined2 *)(&DAT_0097fb86 + iVar1);
  *DAT_0095d4d4 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar1];
  *(undefined2 *)(puVar2 + 3) = *(undefined2 *)(&DAT_0097fb84 + iVar1);
  *(undefined2 *)((int)puVar2 + 0xe) = *(undefined2 *)(&DAT_0097fb86 + iVar1);
  *(undefined2 *)(puVar2 + 4) = *(undefined2 *)(&DAT_0097fb82 + iVar1);
  *(undefined2 *)((int)puVar2 + 10) = 0;
  if ((DAT_0095f6d0 == '\x02') || ((DAT_008e12ac & 0xa00) != 0)) {
    *(undefined2 *)((int)puVar2 + 10) = 1;
  }
  FUN_0047f1e0(DAT_0095d53c,0);
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 2;
}
```

## Command 0x3E
### Official name: filtPri
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x3E_filtPri(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  int iVar1;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  DAT_0095f9c4 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar1));
  FUN_00436040(DAT_0095f9c4);
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x40
### Official name: charInit
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x40_charInit(int *param_1,undefined4 param_2,int param_3,int *param_4)
{
  byte bVar1;
  int iVar2;
  undefined uVar3;
  short sVar4;
  int iVar5;
  byte bVar6;
  undefined2 *puVar7;
  char *pcVar8;
  uint local_8;
  
  iVar2 = *param_4;
  bVar1 = (&DAT_0097fb82)[iVar2];
  bVar6 = (&DAT_0097fb83)[iVar2] & 3;
  local_8 = bVar1 & 0xf;
  if (*param_1 == 0) {
    puVar7 = (undefined2 *)(&DAT_0097fb84 + iVar2);
    sVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
    if (sVar4 == 0x4000) {
      local_8 = 6;
      iVar5 = 0;
      do {
        *(char *)(param_3 + 4 + iVar5) = (char)iVar5;
        iVar5 = iVar5 + 1;
      } while (iVar5 < 6);
    }
    else {
      iVar5 = 0;
      if ((bVar1 & 0xf) != 0) {
        do {
          uVar3 = commandArgParser(*puVar7);
          *(undefined *)(param_3 + 4 + iVar5) = uVar3;
          iVar5 = iVar5 + 1;
          puVar7 = puVar7 + 1;
        } while (iVar5 < (int)local_8);
      }
    }
    if (local_8 != 0) {
      pcVar8 = (char *)(param_3 + 4);
      do {
        (&DAT_0095f730)[*pcVar8 * 0x1c] = 1;
        (&DAT_0095f734)[*pcVar8 * 0xe] = 0;
        (&DAT_0095f736)[*pcVar8 * 0xe] = 0;
        (&DAT_0095f73c)[*pcVar8 * 0xe] = 0x100;
        (&DAT_0095f73e)[*pcVar8 * 0xe] = 0x100;
        (&DAT_0095f738)[*pcVar8 * 0xe] = 0x140;
        (&DAT_0095f73a)[*pcVar8 * 0xe] = 0x1c0;
        (&DAT_0095f740)[*pcVar8 * 0xe] = 0;
        (&DAT_0095f72e)[*pcVar8 * 0xe] = 0;
        FUN_004319b0((int)*pcVar8,bVar6,1);
        FUN_00431ee0((int)*pcVar8,bVar6,0);
        FUN_00431a00((int)*pcVar8,bVar6,0,0);
        FUN_00431a70((int)*pcVar8,bVar6,0x100,0x100);
        FUN_00431ae0((int)*pcVar8,bVar6,0x140,0x1c0);
        FUN_00431b50((int)*pcVar8,bVar6,0);
        pcVar8 = pcVar8 + 1;
        local_8 = local_8 - 1;
      } while (local_8 != 0);
    }
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 1;
  }
  return 0;
}
```

## Command 0x42
### Official name: charDisplay
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x42_charDisplay(int *param_1,undefined4 param_2,int *param_3,int *param_4)
{
  byte bVar1;
  int iVar2;
  char cVar3;
  uint *puVar4;
  char cVar5;
  undefined uVar6;
  undefined2 uVar7;
  int iVar8;
  uint uVar9;
  undefined2 extraout_var;
  undefined2 extraout_var_00;
  undefined2 *puVar10;
  undefined2 *puVar11;
  short *psVar12;
  int *piVar13;
  short *psVar14;
  
  iVar8 = *param_1;
  iVar2 = *param_4;
  if (iVar8 == 0) {
    *param_3 = 0;
    cVar3 = '\0';
    if ((DAT_0095f6d0 == '\x02') && (DAT_042b52d7 != '\0')) {
      cVar3 = DAT_042b52d7;
    }
    if ((&DAT_0097fb82)[iVar2] != '\0') {
      piVar13 = param_3 + 1;
      puVar11 = (undefined2 *)((int)param_3 + 0x16);
      puVar10 = (undefined2 *)(&DAT_0097fb88 + iVar2);
      do {
        cVar5 = commandArgParser(puVar10[-1]);
        *(char *)piVar13 = cVar5;
        puVar11[-6] = (&DAT_0095f72c)[cVar5 * 0xe];
        uVar7 = commandArgParser(*puVar10);
        *puVar11 = uVar7;
        bVar1 = (&DAT_0097fb82)[iVar2];
        (&DAT_0095f72c)[*(char *)piVar13 * 0xe] = uVar7;
        piVar13 = (int *)((int)piVar13 + 1);
        puVar11 = puVar11 + 1;
        puVar10 = puVar10 + 2;
      } while ((-4 - (int)param_3) + (int)piVar13 < (int)(uint)bVar1);
    }
    puVar4 = DAT_0095d4d4;
    *DAT_0095d4d4 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar2];
    iVar8 = 0;
    *(ushort *)(puVar4 + 2) = (ushort)(byte)(&DAT_0097fb82)[iVar2];
    *(undefined2 *)((int)puVar4 + 10) = 0;
    if ((DAT_0095f6d0 == '\x02') || ((DAT_008e12ac & 0xa00) != 0)) {
      *(undefined2 *)((int)puVar4 + 10) = 1;
    }
    if ((&DAT_0097fb82)[iVar2] != '\0') {
      psVar12 = (short *)((int)param_3 + 0x16);
      psVar14 = (short *)((int)puVar4 + 0xe);
      do {
        cVar5 = *(char *)((int)param_3 + iVar8 + 4);
        psVar14[-1] = (short)cVar5;
        *psVar14 = *psVar12;
        *(char *)(psVar14 + 1) = cVar3;
        uVar9 = commandArgParser(CONCAT22((undefined2)(cVar5 >> 7),
                                          (short)(char)(&DAT_0097fb83)[iVar2]));
        if ((short)uVar9 == 0) {
          uVar6 = FUN_00452c20((int)psVar12[-6],(int)*psVar12);
          uVar7 = extraout_var;
        }
        else {
          uVar6 = commandArgParser(uVar9 & 0xffff0000 |
                                   (uint)(ushort)(short)(char)(&DAT_0097fb83)[iVar2]);
          uVar7 = extraout_var_00;
        }
        *(undefined *)(psVar14 + 9) = uVar6;
        uVar6 = commandArgParser(CONCAT22(uVar7,(ushort)(byte)(&DAT_0097fb84)[iVar2]));
        *(undefined *)((int)psVar14 + 0x13) = uVar6;
        iVar8 = iVar8 + 1;
        psVar12 = psVar12 + 1;
        psVar14 = psVar14 + 0xb;
      } while (iVar8 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    }
    FUN_0047f1e0(DAT_0095d53c,0);
    *param_1 = *param_1 + 1;
  }
  else if (iVar8 == 1) {
    iVar8 = FUN_0047f640(DAT_0095d538,1);
    if (iVar8 != 0) {
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
      return 2;
    }
  }
  else if ((iVar8 == 10) && (((byte)DAT_008e12b4 & 8) != 0)) {
    *param_1 = 1;
    *param_3 = *param_3 + 1;
    return 0;
  }
  *param_3 = *param_3 + 1;
  return 0;
}

```
## Command 0x44
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x44(int *param_1,undefined4 param_2,int param_3,int *param_4)
{
  byte bVar1;
  byte bVar2;
  int iVar3;
  char cVar4;
  short sVar5;
  short sVar6;
  short sVar7;
  uint uVar8;
  undefined2 *puVar9;
  short *psVar10;
  int iVar11;
  char *pcVar12;
  
  iVar3 = *param_4;
  bVar1 = (&DAT_0097fb82)[iVar3];
  bVar2 = (&DAT_0097fb83)[iVar3];
  uVar8 = bVar1 & 0xf;
  if (*param_1 != 0) {
    return 0;
  }
  if ((bVar2 & 0x30) == 0) {
    if ((bVar1 & 0xf) != 0) {
      puVar9 = (undefined2 *)(&DAT_0097fb86 + iVar3);
      pcVar12 = (char *)(param_3 + 4);
      psVar10 = (short *)(param_3 + 10);
      do {
        cVar4 = commandArgParser(puVar9[-1]);
        *pcVar12 = cVar4;
        sVar5 = commandArgParser(*puVar9);
        *psVar10 = sVar5;
        sVar6 = commandArgParser(puVar9[1]);
        psVar10[1] = sVar6;
        sVar5 = (&DAT_0095f72c)[*pcVar12 * 0xe];
        if (*psVar10 == 0x4000) {
          if (sVar5 < 0) {
            sVar7 = *(short *)((int)&PTR_DAT_004f5472 + uVar8 * 2);
            sVar7 = (short)((int)(0x280 - (uVar8 - 1) * (int)sVar7) / 2) +
                    ((short)(-4 - param_3) + (short)pcVar12) * sVar7;
          }
          else {
            sVar7 = (&DAT_0095f734)[*pcVar12 * 0xe];
          }
          *psVar10 = sVar7;
        }
        if (sVar6 == 0x4000) {
          if (sVar5 < 0) {
            sVar5 = 0;
          }
          else {
            sVar5 = (&DAT_0095f736)[*pcVar12 * 0xe];
          }
          psVar10[1] = sVar5;
        }
        (&DAT_0095f734)[*pcVar12 * 0xe] = *psVar10;
        cVar4 = *pcVar12;
        pcVar12 = pcVar12 + 1;
        (&DAT_0095f736)[cVar4 * 0xe] = psVar10[1];
        puVar9 = puVar9 + 3;
        psVar10 = psVar10 + 2;
      } while ((int)(pcVar12 + (-4 - param_3)) < (int)uVar8);
    }
    iVar11 = 0;
    if ((bVar1 & 0xf) != 0) {
      puVar9 = (undefined2 *)(param_3 + 10);
      do {
        FUN_00431a00((int)*(char *)(param_3 + 4 + iVar11),bVar2 & 3,*puVar9,puVar9[1]);
        iVar11 = iVar11 + 1;
        puVar9 = puVar9 + 2;
      } while (iVar11 < (int)uVar8);
    }
  }
  else if (((bVar2 & 0x30) == 0x10) && ((bVar1 & 0xf) != 0)) {
    pcVar12 = (char *)(param_3 + 4);
    psVar10 = (short *)(&DAT_0097fb86 + iVar3);
    do {
      cVar4 = commandArgParser(psVar10[-1]);
      *pcVar12 = cVar4;
      if (*psVar10 != 0) {
        FUN_0044f060(*psVar10,(int)(short)(&DAT_0095f734)[cVar4 * 0xe]);
      }
      if (psVar10[1] != 0) {
        FUN_0044f060(psVar10[1],(int)(short)(&DAT_0095f736)[*pcVar12 * 0xe]);
      }
      pcVar12 = pcVar12 + 1;
      psVar10 = psVar10 + 3;
      uVar8 = uVar8 - 1;
    } while (uVar8 != 0);
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar3];
  return 1;
}
```

## Command 0x45
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
void command_0x45(undefined4 param_1,undefined4 param_2,undefined4 param_3,int *param_4)

{
  short sVar1;
  
  sVar1 = commandArgParser((uint)(&scriptBeginAddress_0x97fb80 + *param_4) & 0xffff0000 |
                           (uint)(ushort)(short)(char)(&DAT_0097fb83)[*param_4]);
  if (-1 < sVar1) {
    FUN_00453750(param_3);
    return;
  }
  FUN_00453a20(param_4);
  return;
}
```

## Command 0x46
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x46(int *param_1,undefined4 param_2,int param_3,int *param_4)

{
  short *psVar1;
  byte bVar2;
  byte bVar3;
  int iVar4;
  char cVar5;
  short sVar6;
  short sVar7;
  short sVar8;
  uint uVar9;
  short *psVar10;
  int iVar11;
  char *pcVar12;
  undefined2 *puVar13;
  
  iVar4 = *param_4;
  bVar2 = (&DAT_0097fb82)[iVar4];
  bVar3 = (&DAT_0097fb83)[iVar4];
  uVar9 = bVar2 & 0xf;
  if (*param_1 != 0) {
    return 0;
  }
  if ((bVar3 & 0x30) == 0) {
    if ((bVar2 & 0xf) != 0) {
      pcVar12 = (char *)(param_3 + 4);
      psVar10 = (short *)(param_3 + 10);
      puVar13 = (undefined2 *)(&DAT_0097fb86 + iVar4);
      param_1 = (int *)uVar9;
      do {
        cVar5 = commandArgParser(puVar13[-1]);
        *pcVar12 = cVar5;
        sVar6 = commandArgParser(*puVar13);
        *psVar10 = sVar6;
        sVar7 = commandArgParser(puVar13[1]);
        psVar10[1] = sVar7;
        sVar6 = (&DAT_0095f72c)[*pcVar12 * 0xe];
        if (*psVar10 == 0x4000) {
          if (sVar6 < 0) {
            sVar8 = 0x100;
          }
          else {
            sVar8 = (&DAT_0095f73c)[*pcVar12 * 0xe];
          }
          *psVar10 = sVar8;
        }
        if (sVar7 == 0x4000) {
          if (sVar6 < 0) {
            sVar6 = 0x100;
          }
          else {
            sVar6 = (&DAT_0095f73e)[*pcVar12 * 0xe];
          }
          psVar10[1] = sVar6;
        }
        (&DAT_0095f73c)[*pcVar12 * 0xe] = *psVar10;
        cVar5 = *pcVar12;
        psVar1 = psVar10 + 1;
        puVar13 = puVar13 + 3;
        psVar10 = psVar10 + 2;
        pcVar12 = pcVar12 + 1;
        param_1 = (int *)((int)param_1 - 1);
        (&DAT_0095f73e)[cVar5 * 0xe] = *psVar1;
      } while (param_1 != (int *)0x0);
    }
    iVar11 = 0;
    if ((bVar2 & 0xf) != 0) {
      puVar13 = (undefined2 *)(param_3 + 10);
      do {
        FUN_00431a70((int)*(char *)(param_3 + 4 + iVar11),bVar3 & 3,*puVar13,puVar13[1]);
        iVar11 = iVar11 + 1;
        puVar13 = puVar13 + 2;
      } while (iVar11 < (int)uVar9);
    }
  }
  else if (((bVar3 & 0x30) == 0x10) && ((bVar2 & 0xf) != 0)) {
    pcVar12 = (char *)(param_3 + 4);
    psVar10 = (short *)(&DAT_0097fb86 + iVar4);
    do {
      cVar5 = commandArgParser(psVar10[-1]);
      *pcVar12 = cVar5;
      if (*psVar10 != 0) {
        FUN_0044f060(*psVar10,(int)(short)(&DAT_0095f73c)[cVar5 * 0xe]);
      }
      if (psVar10[1] != 0) {
        FUN_0044f060(psVar10[1],(int)(short)(&DAT_0095f73e)[*pcVar12 * 0xe]);
      }
      pcVar12 = pcVar12 + 1;
      psVar10 = psVar10 + 3;
      uVar9 = uVar9 - 1;
    } while (uVar9 != 0);
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar4];
  return 1;
}
```

## Command 0x47
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
void command_0x47(undefined4 param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  short sVar1;
  
  sVar1 = commandArgParser((uint)(&scriptBeginAddress_0x97fb80 + *param_4) & 0xffff0000 |
                           (uint)(ushort)(short)(char)(&DAT_0097fb83)[*param_4]);
  if (-1 < sVar1) {
    FUN_00453d00();
    return;
  }
  FUN_00453f90(param_1,param_2,param_3,param_4);
  return;
}
```

## Command 0x48
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x48(int *param_1,undefined4 param_2,int param_3,int *param_4)
{
  short *psVar1;
  byte bVar2;
  byte bVar3;
  int iVar4;
  char cVar5;
  short sVar6;
  short sVar7;
  short sVar8;
  uint uVar9;
  short *psVar10;
  int iVar11;
  char *pcVar12;
  undefined2 *puVar13;
  
  iVar4 = *param_4;
  bVar2 = (&DAT_0097fb82)[iVar4];
  bVar3 = (&DAT_0097fb83)[iVar4];
  uVar9 = bVar2 & 0xf;
  if (*param_1 != 0) {
    return 0;
  }
  if ((bVar3 & 0x30) == 0) {
    if ((bVar2 & 0xf) != 0) {
      pcVar12 = (char *)(param_3 + 4);
      psVar10 = (short *)(param_3 + 10);
      puVar13 = (undefined2 *)(&DAT_0097fb86 + iVar4);
      param_1 = (int *)uVar9;
      do {
        cVar5 = commandArgParser(puVar13[-1]);
        *pcVar12 = cVar5;
        sVar6 = commandArgParser(*puVar13);
        *psVar10 = sVar6;
        sVar7 = commandArgParser(puVar13[1]);
        psVar10[1] = sVar7;
        sVar6 = (&DAT_0095f72c)[*pcVar12 * 0xe];
        if (*psVar10 == 0x4000) {
          if (sVar6 < 0) {
            sVar8 = 0x140;
          }
          else {
            sVar8 = (&DAT_0095f738)[*pcVar12 * 0xe];
          }
          *psVar10 = sVar8;
        }
        if (sVar7 == 0x4000) {
          if (sVar6 < 0) {
            sVar6 = 0x1c0;
          }
          else {
            sVar6 = (&DAT_0095f73a)[*pcVar12 * 0xe];
          }
          psVar10[1] = sVar6;
        }
        (&DAT_0095f738)[*pcVar12 * 0xe] = *psVar10;
        cVar5 = *pcVar12;
        psVar1 = psVar10 + 1;
        puVar13 = puVar13 + 3;
        psVar10 = psVar10 + 2;
        pcVar12 = pcVar12 + 1;
        param_1 = (int *)((int)param_1 - 1);
        (&DAT_0095f73a)[cVar5 * 0xe] = *psVar1;
      } while (param_1 != (int *)0x0);
    }
    iVar11 = 0;
    if ((bVar2 & 0xf) != 0) {
      puVar13 = (undefined2 *)(param_3 + 10);
      do {
        FUN_00431ae0((int)*(char *)(param_3 + 4 + iVar11),bVar3 & 3,*puVar13,puVar13[1]);
        iVar11 = iVar11 + 1;
        puVar13 = puVar13 + 2;
      } while (iVar11 < (int)uVar9);
    }
  }
  else if (((bVar3 & 0x30) == 0x10) && ((bVar2 & 0xf) != 0)) {
    pcVar12 = (char *)(param_3 + 4);
    psVar10 = (short *)(&DAT_0097fb86 + iVar4);
    do {
      cVar5 = commandArgParser(psVar10[-1]);
      *pcVar12 = cVar5;
      if (*psVar10 != 0) {
        FUN_0044f060(*psVar10,(int)(short)(&DAT_0095f738)[cVar5 * 0xe]);
      }
      if (psVar10[1] != 0) {
        FUN_0044f060(psVar10[1],(int)(short)(&DAT_0095f73a)[*pcVar12 * 0xe]);
      }
      pcVar12 = pcVar12 + 1;
      psVar10 = psVar10 + 3;
      uVar9 = uVar9 - 1;
    } while (uVar9 != 0);
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar4];
  return 1;
}
```

## Command 0x49
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
void command_0x49(undefined4 param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  short sVar1;
  
  sVar1 = commandArgParser((uint)(&scriptBeginAddress_0x97fb80 + *param_4) & 0xffff0000 |
                           (uint)(ushort)(short)(char)(&DAT_0097fb83)[*param_4]);
  if (-1 < sVar1) {
    FUN_00454270(param_3);
    return;
  }
  FUN_00454500(param_4);
  return;
}
```

## Command 0x4A
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x4A(int *param_1,undefined4 param_2,int param_3,int *param_4)
{
  byte bVar1;
  byte bVar2;
  int iVar3;
  char cVar4;
  short sVar5;
  uint uVar6;
  char *pcVar7;
  int iVar8;
  short *psVar9;
  undefined2 *puVar10;
  
  iVar3 = *param_4;
  bVar1 = (&DAT_0097fb82)[iVar3];
  bVar2 = (&DAT_0097fb83)[iVar3];
  uVar6 = bVar1 & 0xf;
  if (*param_1 != 0) {
    return 0;
  }
  if ((bVar2 & 0x30) == 0) {
    if ((bVar1 & 0xf) != 0) {
      pcVar7 = (char *)(param_3 + 4);
      psVar9 = (short *)(param_3 + 10);
      puVar10 = (undefined2 *)(&DAT_0097fb86 + iVar3);
      param_1 = (int *)uVar6;
      do {
        cVar4 = commandArgParser(puVar10[-1]);
        *pcVar7 = cVar4;
        sVar5 = commandArgParser(*puVar10);
        *psVar9 = sVar5;
        if (sVar5 == 0x4000) {
          if ((short)(&DAT_0095f72c)[*pcVar7 * 0xe] < 0) {
            sVar5 = 0;
          }
          else {
            sVar5 = (&DAT_0095f740)[*pcVar7 * 0xe];
          }
          *psVar9 = sVar5;
        }
        cVar4 = *pcVar7;
        sVar5 = *psVar9;
        psVar9 = psVar9 + 1;
        puVar10 = puVar10 + 2;
        pcVar7 = pcVar7 + 1;
        param_1 = (int *)((int)param_1 - 1);
        (&DAT_0095f740)[cVar4 * 0xe] = sVar5;
      } while (param_1 != (int *)0x0);
    }
    iVar8 = 0;
    if ((bVar1 & 0xf) != 0) {
      puVar10 = (undefined2 *)(param_3 + 10);
      do {
        FUN_00431b50((int)*(char *)(param_3 + 4 + iVar8),bVar2 & 3,*puVar10);
        iVar8 = iVar8 + 1;
        puVar10 = puVar10 + 1;
      } while (iVar8 < (int)uVar6);
    }
  }
  else if (((bVar2 & 0x30) == 0x10) && (iVar8 = 0, (bVar1 & 0xf) != 0)) {
    psVar9 = (short *)(&DAT_0097fb86 + iVar3);
    do {
      cVar4 = commandArgParser(psVar9[-1]);
      *(char *)(param_3 + 4 + iVar8) = cVar4;
      if (*psVar9 != 0) {
        FUN_0044f060(*psVar9,(int)(short)(&DAT_0095f740)[cVar4 * 0xe]);
      }
      iVar8 = iVar8 + 1;
      psVar9 = psVar9 + 2;
    } while (iVar8 < (int)uVar6);
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar3];
  return 1;
}
```

## Command 0x4B
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
void command_0x4B(undefined4 param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  short sVar1;
  
  sVar1 = commandArgParser((uint)(&scriptBeginAddress_0x97fb80 + *param_4) & 0xffff0000 |
                           (uint)(ushort)(short)(char)(&DAT_0097fb83)[*param_4]);
  if (-1 < sVar1) {
    FUN_00454740(param_3);
    return;
  }
  FUN_00454940(param_3,param_4);
  return;
}
```

## Command 0x4C
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x4C(int *param_1,undefined4 param_2,int param_3,int *param_4)
{
  ushort *puVar1;
  byte bVar2;
  undefined2 uVar3;
  int iVar4;
  char cVar5;
  byte bVar6;
  short sVar7;
  ushort uVar8;
  int iVar9;
  undefined4 uVar10;
  int iVar11;
  undefined2 *puVar12;
  uint uVar13;
  char *pcVar14;
  ushort *puVar15;
  short *psVar16;
  
  iVar4 = *param_4;
  bVar2 = (&DAT_0097fb83)[iVar4];
  if (*param_1 != 0) {
    return 0;
  }
  switch(bVar2 & 0x30) {
  case 0:
  case 0x20:
  case 0x30:
    puVar12 = (undefined2 *)(&DAT_0097fb84 + iVar4);
    sVar7 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar4));
    if (sVar7 == 0x4000) {
      param_1 = (int *)0x6;
      iVar9 = 0;
      do {
        *(char *)(param_3 + 4 + iVar9) = (char)iVar9;
        iVar9 = iVar9 + 1;
      } while (iVar9 < 6);
    }
    else {
      param_1 = (int *)(uint)(byte)(&DAT_0097fb82)[iVar4];
      iVar9 = 0;
      if (param_1 != (int *)0x0) {
        do {
          cVar5 = commandArgParser(*puVar12);
          *(char *)(param_3 + 4 + iVar9) = cVar5;
          FID_conflict:_wprintf("ChrCol Cid:%d\n",(int)cVar5);
          iVar9 = iVar9 + 1;
          puVar12 = puVar12 + 5;
        } while (iVar9 < (int)param_1);
      }
    }
    bVar6 = (&DAT_0097fb83)[iVar4] & 0x30;
    if (((&DAT_0097fb83)[iVar4] & 0x30) == 0) {
      if (param_1 == (int *)0x0) break;
      pcVar14 = (char *)(param_3 + 4);
      puVar12 = (undefined2 *)(&DAT_0097fb88 + iVar4);
      puVar15 = (ushort *)(param_3 + 0xc);
      uVar13 = (uint)param_1;
      do {
        sVar7 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar4));
        if (sVar7 == 0x4000) {
          uVar8 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar4));
          puVar15[-1] = uVar8;
          uVar8 = commandArgParser(*(undefined2 *)(&DAT_0097fb88 + iVar4));
          *puVar15 = uVar8;
          uVar8 = commandArgParser(*(undefined2 *)(&DAT_0097fb8a + iVar4));
          puVar15[1] = uVar8;
          uVar3 = *(undefined2 *)(&DAT_0097fb8c + iVar4);
        }
        else {
          uVar8 = commandArgParser(puVar12[-1]);
          puVar15[-1] = uVar8;
          uVar8 = commandArgParser(*puVar12);
          *puVar15 = uVar8;
          uVar8 = commandArgParser(puVar12[1]);
          puVar15[1] = uVar8;
          uVar3 = puVar12[2];
        }
        uVar8 = commandArgParser(uVar3);
        puVar15[2] = uVar8;
        if (puVar15[-1] == 0x4000) {
          puVar15[-1] = (ushort)(byte)(&DAT_0095f742)[*pcVar14 * 0x1c];
        }
        if (*puVar15 == 0x4000) {
          *puVar15 = (ushort)(byte)(&DAT_0095f743)[*pcVar14 * 0x1c];
        }
        if (puVar15[1] == 0x4000) {
          puVar15[1] = (ushort)(byte)(&DAT_0095f744)[*pcVar14 * 0x1c];
        }
        if (puVar15[2] == 0x4000) {
          puVar15[2] = (ushort)(byte)(&DAT_0095f745)[*pcVar14 * 0x1c];
        }
        (&DAT_0095f742)[*pcVar14 * 0x1c] = *(undefined *)(puVar15 + -1);
        (&DAT_0095f743)[*pcVar14 * 0x1c] = *(undefined *)puVar15;
        (&DAT_0095f744)[*pcVar14 * 0x1c] = *(undefined *)(puVar15 + 1);
        cVar5 = *pcVar14;
        puVar1 = puVar15 + 2;
        puVar12 = puVar12 + 5;
        puVar15 = puVar15 + 4;
        pcVar14 = pcVar14 + 1;
        uVar13 = uVar13 - 1;
        (&DAT_0095f745)[cVar5 * 0x1c] = *(undefined *)puVar1;
      } while (uVar13 != 0);
    }
    else if (bVar6 == 0x20) {
      if (param_1 == (int *)0x0) break;
      pcVar14 = (char *)(param_3 + 4);
      uVar13 = (uint)param_1;
      psVar16 = (short *)(&DAT_0097fb86 + iVar4);
      do {
        sVar7 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar4));
        if (sVar7 == 0x4000) {
          *(undefined4 *)(&DAT_0095f742 + *pcVar14 * 0x1c) =
               *(undefined4 *)(DAT_0095fb18 + *(short *)(&DAT_0097fb86 + iVar4) * 4);
        }
        else {
          *(undefined4 *)(&DAT_0095f742 + *pcVar14 * 0x1c) =
               *(undefined4 *)(DAT_0095fb18 + *psVar16 * 4);
        }
        psVar16 = psVar16 + 2;
        pcVar14 = pcVar14 + 1;
        uVar13 = uVar13 - 1;
      } while (uVar13 != 0);
    }
    else if (bVar6 == 0x30) {
      if (param_1 == (int *)0x0) break;
      pcVar14 = (char *)(param_3 + 4);
      uVar13 = (uint)param_1;
      puVar12 = (undefined2 *)(&DAT_0097fb86 + iVar4);
      do {
        sVar7 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar4));
        if (sVar7 == 0x4000) {
          uVar10 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar4));
          sVar7 = FUN_00452ea0(uVar10);
          *(undefined4 *)(&DAT_0095f742 + *pcVar14 * 0x1c) =
               *(undefined4 *)(DAT_0095fb18 + sVar7 * 4);
        }
        else {
          uVar10 = commandArgParser(*puVar12);
          sVar7 = FUN_00452ea0(uVar10);
          *(undefined4 *)(&DAT_0095f742 + *pcVar14 * 0x1c) =
               *(undefined4 *)(DAT_0095fb18 + sVar7 * 4);
        }
        puVar12 = puVar12 + 2;
        pcVar14 = pcVar14 + 1;
        uVar13 = uVar13 - 1;
      } while (uVar13 != 0);
    }
    if (param_1 != (int *)0x0) {
      pcVar14 = (char *)(param_3 + 4);
      do {
        iVar11 = (int)*pcVar14;
        iVar9 = iVar11 * 0x1c;
        FUN_00431da0(iVar11,bVar2 & 3,(&DAT_0095f742)[iVar9],(&DAT_0095f743)[iVar9],
                     (&DAT_0095f744)[iVar9],(&DAT_0095f745)[iVar11 * 0x1c]);
        pcVar14 = pcVar14 + 1;
        param_1 = (int *)((int)param_1 - 1);
      } while (param_1 != (int *)0x0);
    }
    break;
  case 0x10:
    if ((&DAT_0097fb82)[iVar4] != '\0') {
      pcVar14 = (char *)(param_3 + 4);
      psVar16 = (short *)(&DAT_0097fb86 + iVar4);
      do {
        cVar5 = commandArgParser(psVar16[-1]);
        *pcVar14 = cVar5;
        if (*psVar16 != 0) {
          FUN_0044f060(*psVar16,(&DAT_0095f742)[cVar5 * 0x1c]);
        }
        if (psVar16[1] != 0) {
          FUN_0044f060(psVar16[1],(&DAT_0095f743)[*pcVar14 * 0x1c]);
        }
        if (psVar16[2] != 0) {
          FUN_0044f060(psVar16[2],(&DAT_0095f744)[*pcVar14 * 0x1c]);
        }
        if (psVar16[3] != 0) {
          FUN_0044f060(psVar16[3],(&DAT_0095f745)[*pcVar14 * 0x1c]);
        }
        pcVar14 = pcVar14 + 1;
        psVar16 = psVar16 + 5;
      } while ((int)(pcVar14 + (-4 - param_3)) < (int)(uint)(byte)(&DAT_0097fb82)[iVar4]);
    }
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar4];
  return 1;
}
```

## Command 0x4D
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
void command_0x4D(undefined4 param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  short sVar1;
  
  sVar1 = commandArgParser((uint)(&scriptBeginAddress_0x97fb80 + *param_4) & 0xffff0000 |
                           (uint)(ushort)(short)(char)(&DAT_0097fb83)[*param_4]);
  if (-1 < sVar1) {
    FUN_00454f60(param_3);
    return;
  }
  FUN_004552f0(param_4);
  return;
}
```

## Command 0x50
### Official name: charNo
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x50_charNo(int *param_1,undefined4 param_2,int param_3,int *param_4)
{
  ushort uVar1;
  int iVar2;
  char cVar3;
  uint uVar4;
  ushort *puVar5;
  int iVar6;
  
  iVar2 = *param_4;
  if (*param_1 == 0) {
    if ((((&DAT_0097fb85)[iVar2] & 0x30) == 0x10) && (iVar6 = 0, (&DAT_0097fb82)[iVar2] != '\0')) {
      puVar5 = (ushort *)(&DAT_0097fb88 + iVar2);
      do {
        cVar3 = commandArgParser(puVar5[-1]);
        *(char *)(iVar6 + 4 + param_3) = cVar3;
        uVar1 = *puVar5;
        if (uVar1 != 0) {
          uVar4 = (uint)uVar1;
          if ((ushort)(uVar1 + 0x8000) < 0x1000) {
            if ((uVar4 & 0xfff) < 0x800) {
              (&DAT_0095d860)[uVar4 & 0x7ff] = (&DAT_0095f72c)[cVar3 * 0xe];
            }
            else {
              (&DAT_0095d560)[uVar4 & 0x7ff] = (byte)(&DAT_0095f72c)[cVar3 * 0xe] & 1;
            }
          }
        }
        iVar6 = iVar6 + 1;
        puVar5 = puVar5 + 2;
      } while (iVar6 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    }
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 1;
  }
  return 0;
}
```

## Command 0x51
### Official name: charOn
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x51_charOn(int *param_1,undefined4 param_2,uint param_3,int *param_4)
{
  byte bVar1;
  int iVar2;
  char cVar3;
  undefined uVar4;
  short sVar5;
  undefined2 uVar6;
  uint uVar7;
  int iVar8;
  int iVar9;
  undefined2 *puVar10;
  undefined2 *puVar11;
  short *psVar12;
  char *pcVar13;
  
  iVar8 = param_3;
  iVar2 = *param_4;
  bVar1 = (&DAT_0097fb83)[iVar2];
  if (*param_1 == 0) {
    if ((bVar1 & 0x30) == 0) {
      sVar5 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
      if (sVar5 == 0x4000) {
        param_3 = 6;
        iVar9 = 0;
        puVar10 = (undefined2 *)(iVar8 + 10);
        do {
          *(char *)(iVar9 + 4 + iVar8) = (char)iVar9;
          uVar6 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar2));
          *puVar10 = uVar6;
          iVar9 = iVar9 + 1;
          puVar10 = puVar10 + 1;
          uVar7 = param_3;
        } while (iVar9 < 6);
      }
      else {
        uVar7 = (uint)(byte)(&DAT_0097fb82)[iVar2];
        iVar9 = 0;
        if (uVar7 != 0) {
          puVar10 = (undefined2 *)(param_3 + 10);
          puVar11 = (undefined2 *)(&DAT_0097fb86 + iVar2);
          do {
            uVar4 = commandArgParser(puVar11[-1]);
            *(undefined *)(iVar9 + 4 + param_3) = uVar4;
            uVar6 = commandArgParser(*puVar11);
            *puVar10 = uVar6;
            iVar9 = iVar9 + 1;
            puVar10 = puVar10 + 1;
            puVar11 = puVar11 + 2;
          } while (iVar9 < (int)uVar7);
        }
      }
      param_3 = uVar7;
      if (param_3 != 0) {
        pcVar13 = (char *)(iVar8 + 4);
        puVar10 = (undefined2 *)(iVar8 + 10);
        do {
          (&DAT_0095f730)[*pcVar13 * 0x1c] = *(undefined *)puVar10;
          FUN_004319b0((int)*pcVar13,bVar1 & 3,*puVar10);
          puVar10 = puVar10 + 1;
          pcVar13 = pcVar13 + 1;
          param_3 = param_3 - 1;
        } while (param_3 != 0);
      }
    }
    else if (((bVar1 & 0x30) == 0x10) && (iVar8 = 0, (&DAT_0097fb82)[iVar2] != '\0')) {
      psVar12 = (short *)(&DAT_0097fb86 + iVar2);
      do {
        cVar3 = commandArgParser(psVar12[-1]);
        *(char *)(iVar8 + 4 + param_3) = cVar3;
        if (*psVar12 != 0) {
          FUN_0044f060(*psVar12,(int)(char)(&DAT_0095f730)[cVar3 * 0x1c]);
        }
        iVar8 = iVar8 + 1;
        psVar12 = psVar12 + 2;
      } while (iVar8 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    }
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 1;
  }
  return 0;
}
```

## Command 0x52
### Official name: charPri
### My guess: (N/A)

### Code
```cpp
{
  byte bVar1;
  int iVar2;
  char cVar3;
  undefined uVar4;
  short sVar5;
  undefined2 uVar6;
  uint uVar7;
  int iVar8;
  int iVar9;
  undefined2 *puVar10;
  undefined2 *puVar11;
  short *psVar12;
  char *pcVar13;
  
  iVar8 = param_3;
  iVar2 = *param_4;
  bVar1 = (&DAT_0097fb83)[iVar2];
  if (*param_1 == 0) {
    if ((bVar1 & 0x30) == 0) {
      sVar5 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
      if (sVar5 == 0x4000) {
        param_3 = 6;
        iVar9 = 0;
        puVar10 = (undefined2 *)(iVar8 + 10);
        do {
          *(char *)(iVar9 + 4 + iVar8) = (char)iVar9;
          uVar6 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar2));
          *puVar10 = uVar6;
          iVar9 = iVar9 + 1;
          puVar10 = puVar10 + 1;
          uVar7 = param_3;
        } while (iVar9 < 6);
      }
      else {
        uVar7 = (uint)(byte)(&DAT_0097fb82)[iVar2];
        iVar9 = 0;
        if (uVar7 != 0) {
          puVar10 = (undefined2 *)(param_3 + 10);
          puVar11 = (undefined2 *)(&DAT_0097fb86 + iVar2);
          do {
            uVar4 = commandArgParser(puVar11[-1]);
            *(undefined *)(iVar9 + 4 + param_3) = uVar4;
            uVar6 = commandArgParser(*puVar11);
            *puVar10 = uVar6;
            iVar9 = iVar9 + 1;
            puVar10 = puVar10 + 1;
            puVar11 = puVar11 + 2;
          } while (iVar9 < (int)uVar7);
        }
      }
      param_3 = uVar7;
      if (param_3 != 0) {
        pcVar13 = (char *)(iVar8 + 4);
        puVar10 = (undefined2 *)(iVar8 + 10);
        do {
          (&DAT_0095f731)[*pcVar13 * 0x1c] = *(undefined *)puVar10;
          FUN_00431e90((int)*pcVar13,bVar1 & 3,*puVar10);
          puVar10 = puVar10 + 1;
          pcVar13 = pcVar13 + 1;
          param_3 = param_3 - 1;
        } while (param_3 != 0);
      }
    }
    else if (((bVar1 & 0x30) == 0x10) && (iVar8 = 0, (&DAT_0097fb82)[iVar2] != '\0')) {
      psVar12 = (short *)(&DAT_0097fb86 + iVar2);
      do {
        cVar3 = commandArgParser(psVar12[-1]);
        *(char *)(iVar8 + 4 + param_3) = cVar3;
        if (*psVar12 != 0) {
          FUN_0044f060(*psVar12,(int)(char)(&DAT_0095f731)[cVar3 * 0x1c]);
        }
        iVar8 = iVar8 + 1;
        psVar12 = psVar12 + 2;
      } while (iVar8 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    }
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 1;
  }
  return 0;
}
```

## Command 0x53
### Official name: charAnimation
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x53_charAnimation(int *param_1,undefined4 param_2,uint param_3,int *param_4)
{
  int iVar1;
  undefined2 *puVar2;
  char cVar3;
  undefined uVar4;
  short sVar5;
  undefined2 uVar6;
  uint uVar7;
  int iVar8;
  int iVar9;
  char *pcVar10;
  short *psVar11;
  short *psVar12;
  undefined2 *puVar13;
  
  iVar8 = param_3;
  iVar1 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  if (((&DAT_0097fb83)[iVar1] & 0x30) == 0) {
    sVar5 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar1));
    if (sVar5 == 0x4000) {
      param_3 = 6;
      iVar9 = 0;
      puVar13 = (undefined2 *)(iVar8 + 0x16);
      do {
        *(char *)(iVar9 + 4 + iVar8) = (char)iVar9;
        uVar6 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar1));
        puVar13[-6] = uVar6;
        uVar6 = commandArgParser(*(undefined2 *)(&DAT_0097fb88 + iVar1));
        *puVar13 = uVar6;
        iVar9 = iVar9 + 1;
        puVar13 = puVar13 + 1;
        uVar7 = param_3;
      } while (iVar9 < 6);
    }
    else {
      uVar7 = (uint)(byte)(&DAT_0097fb82)[iVar1];
      iVar9 = 0;
      if (uVar7 != 0) {
        puVar13 = (undefined2 *)(param_3 + 0x16);
        puVar2 = (undefined2 *)(&scriptBeginAddress_0x97fb80 + iVar1);
        do {
          uVar4 = commandArgParser(puVar2[2]);
          *(undefined *)(iVar9 + 4 + param_3) = uVar4;
          uVar6 = commandArgParser(puVar2[3]);
          puVar13[-6] = uVar6;
          uVar6 = commandArgParser(puVar2[4]);
          *puVar13 = uVar6;
          iVar9 = iVar9 + 1;
          puVar13 = puVar13 + 1;
          puVar2 = puVar2 + 3;
        } while (iVar9 < (int)uVar7);
      }
    }
    param_3 = uVar7;
    if (param_3 != 0) {
      pcVar10 = (char *)(iVar8 + 4);
      psVar12 = (short *)(iVar8 + 10);
      do {
        (&DAT_0095f746)[(int)*psVar12 + *pcVar10 * 0xe] = psVar12[6];
        FUN_004342b0((int)*pcVar10,(int)*psVar12,psVar12[6]);
        psVar12 = psVar12 + 1;
        pcVar10 = pcVar10 + 1;
        param_3 = param_3 - 1;
      } while (param_3 != 0);
    }
  }
  else if ((((&DAT_0097fb83)[iVar1] & 0x30) == 0x10) && (iVar8 = 0, (&DAT_0097fb82)[iVar1] != '\0'))
  {
    psVar12 = (short *)(&DAT_0097fb88 + iVar1);
    psVar11 = (short *)(param_3 + 10);
    do {
      cVar3 = commandArgParser(psVar12[-2]);
      *(char *)(param_3 + 4 + iVar8) = cVar3;
      if (*psVar12 != 0) {
        FUN_0044f060(*psVar12,(int)(short)(&DAT_0095f746)[(int)*psVar11 + cVar3 * 0xe]);
      }
      iVar8 = iVar8 + 1;
      psVar11 = psVar11 + 1;
      psVar12 = psVar12 + 3;
    } while (iVar8 < (int)(uint)(byte)(&DAT_0097fb82)[iVar1]);
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
    return 1;
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x55
### Official name: charSwap
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x55_charSwap(int *param_1,undefined4 param_2,int param_3,int *param_4)
{
  short sVar1;
  int iVar2;
  undefined2 uVar3;
  short sVar4;
  int iVar5;
  undefined4 *puVar6;
  undefined4 *puVar7;
  undefined4 local_1c [7];
  
  iVar2 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  uVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar2));
  *(undefined2 *)(param_3 + 4) = uVar3;
  sVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
  sVar1 = *(short *)(param_3 + 4);
  *(short *)(param_3 + 6) = sVar4;
  puVar6 = (undefined4 *)(&DAT_0095f72c + sVar1 * 0xe);
  puVar7 = local_1c;
  for (iVar5 = 7; iVar5 != 0; iVar5 = iVar5 + -1) {
    *puVar7 = *puVar6;
    puVar6 = puVar6 + 1;
    puVar7 = puVar7 + 1;
  }
  puVar6 = (undefined4 *)(&DAT_0095f72c + sVar4 * 0xe);
  puVar7 = (undefined4 *)(&DAT_0095f72c + sVar1 * 0xe);
  for (iVar5 = 7; iVar5 != 0; iVar5 = iVar5 + -1) {
    *puVar7 = *puVar6;
    puVar6 = puVar6 + 1;
    puVar7 = puVar7 + 1;
  }
  puVar6 = local_1c;
  puVar7 = (undefined4 *)(&DAT_0095f72c + *(short *)(param_3 + 6) * 0xe);
  for (iVar5 = 7; iVar5 != 0; iVar5 = iVar5 + -1) {
    *puVar7 = *puVar6;
    puVar6 = puVar6 + 1;
    puVar7 = puVar7 + 1;
  }
  FUN_004318f0((int)*(short *)(param_3 + 4),(int)*(short *)(param_3 + 6));
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
  return 1;
}
```

## Command 0x56 0x57
### Official name: charShadow / charReturn
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x56_0x57_charShadow_charRet(int *param_1,undefined4 param_2,int *param_3,int *param_4)
{
  int iVar1;
  uint *puVar2;
  int iVar3;
  
  iVar1 = *param_4;
  if (*param_1 == 0) {
    *param_3 = 0;
    puVar2 = DAT_0095d4d4;
    *DAT_0095d4d4 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar1];
    *(undefined2 *)((int)puVar2 + 10) = 0;
    FUN_0047f1e0(DAT_0095d53c,0);
    *param_1 = *param_1 + 1;
  }
  else if (*param_1 == 1) {
    iVar3 = FUN_0047f640(DAT_0095d538,1);
    if (iVar3 != 0) {
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
      return 2;
    }
  }
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x59
### Official name: charAttack
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x59_charAttack(int *param_1,undefined4 param_2,uint param_3,int *param_4)
{
  byte bVar1;
  int iVar2;
  char cVar3;
  undefined uVar4;
  short sVar5;
  undefined2 uVar6;
  uint uVar7;
  int iVar8;
  int iVar9;
  undefined2 *puVar10;
  undefined2 *puVar11;
  short *psVar12;
  char *pcVar13;
  
  iVar8 = param_3;
  iVar2 = *param_4;
  bVar1 = (&DAT_0097fb83)[iVar2];
  if (*param_1 == 0) {
    if ((bVar1 & 0x30) == 0) {
      sVar5 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
      if (sVar5 == 0x4000) {
        param_3 = 6;
        iVar9 = 0;
        puVar10 = (undefined2 *)(iVar8 + 10);
        do {
          *(char *)(iVar9 + 4 + iVar8) = (char)iVar9;
          uVar6 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar2));
          *puVar10 = uVar6;
          iVar9 = iVar9 + 1;
          puVar10 = puVar10 + 1;
          uVar7 = param_3;
        } while (iVar9 < 6);
      }
      else {
        uVar7 = (uint)(byte)(&DAT_0097fb82)[iVar2];
        iVar9 = 0;
        if (uVar7 != 0) {
          puVar10 = (undefined2 *)(param_3 + 10);
          puVar11 = (undefined2 *)(&DAT_0097fb86 + iVar2);
          do {
            uVar4 = commandArgParser(puVar11[-1]);
            *(undefined *)(iVar9 + 4 + param_3) = uVar4;
            uVar6 = commandArgParser(*puVar11);
            *puVar10 = uVar6;
            iVar9 = iVar9 + 1;
            puVar10 = puVar10 + 1;
            puVar11 = puVar11 + 2;
          } while (iVar9 < (int)uVar7);
        }
      }
      param_3 = uVar7;
      if (param_3 != 0) {
        pcVar13 = (char *)(iVar8 + 4);
        puVar10 = (undefined2 *)(iVar8 + 10);
        do {
          (&DAT_0095f72e)[*pcVar13 * 0xe] = *puVar10;
          FUN_00431ee0((int)*pcVar13,bVar1 & 3,*puVar10);
          puVar10 = puVar10 + 1;
          pcVar13 = pcVar13 + 1;
          param_3 = param_3 - 1;
        } while (param_3 != 0);
      }
    }
    else if (((bVar1 & 0x30) == 0x10) && (iVar8 = 0, (&DAT_0097fb82)[iVar2] != '\0')) {
      psVar12 = (short *)(&DAT_0097fb86 + iVar2);
      do {
        cVar3 = commandArgParser(psVar12[-1]);
        *(char *)(iVar8 + 4 + param_3) = cVar3;
        if (*psVar12 != 0) {
          FUN_0044f060(*psVar12,(int)(short)(&DAT_0095f72e)[cVar3 * 0xe]);
        }
        iVar8 = iVar8 + 1;
        psVar12 = psVar12 + 2;
      } while (iVar8 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    }
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 1;
  }
  return 0;
}
```

## Command 0x5F
### Official name: getbackground
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x5F_getBackground(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  int iVar1;
  uint uVar2;
  short sVar3;
  undefined4 uVar4;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  if ((&DAT_0097fb82)[iVar1] == '\0') {
    sVar3 = *(short *)(&DAT_0097fb84 + iVar1);
  }
  else {
    uVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar1));
    sVar3 = FUN_00452ea0(uVar4);
  }
  uVar2 = *(uint *)(DAT_0095fb18 + sVar3 * 4);
  if (*(short *)(&DAT_0097fb86 + iVar1) != 0) {
    FUN_0044f060(*(short *)(&DAT_0097fb86 + iVar1),uVar2 & 0xff);
  }
  if (*(short *)(&DAT_0097fb88 + iVar1) != 0) {
    FUN_0044f060(*(short *)(&DAT_0097fb88 + iVar1),uVar2 >> 8 & 0xff);
  }
  if (*(short *)(&DAT_0097fb8a + iVar1) != 0) {
    FUN_0044f060(*(short *)(&DAT_0097fb8a + iVar1),uVar2 >> 0x10 & 0xff);
  }
  if (*(short *)(&DAT_0097fb8c + iVar1) != 0) {
    FUN_0044f060(*(short *)(&DAT_0097fb8c + iVar1),uVar2 >> 0x18);
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x60
### Official name: objInit
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x60_objInit(int *param_1,undefined4 param_2,int param_3,int *param_4)
{
  byte bVar1;
  int iVar2;
  undefined uVar3;
  short sVar4;
  int iVar5;
  uint uVar6;
  undefined2 *puVar7;
  char *pcVar8;
  
  iVar2 = *param_4;
  bVar1 = (&DAT_0097fb83)[iVar2];
  if (*param_1 == 0) {
    puVar7 = (undefined2 *)(&DAT_0097fb84 + iVar2);
    sVar4 = commandArgParser(*puVar7);
    if (sVar4 == 0x4000) {
      uVar6 = 8;
      iVar5 = 0;
      do {
        *(char *)(param_3 + 4 + iVar5) = (char)iVar5;
        iVar5 = iVar5 + 1;
      } while (iVar5 < 8);
    }
    else {
      uVar6 = (uint)(byte)(&DAT_0097fb82)[iVar2];
      iVar5 = 0;
      if (uVar6 != 0) {
        do {
          uVar3 = commandArgParser(*puVar7);
          *(undefined *)(param_3 + 4 + iVar5) = uVar3;
          iVar5 = iVar5 + 1;
          puVar7 = puVar7 + 1;
        } while (iVar5 < (int)uVar6);
      }
    }
    if (uVar6 != 0) {
      pcVar8 = (char *)(param_3 + 4);
      do {
        (&DAT_0095f7d8)[*pcVar8 * 0x22] = 1;
        *(undefined2 *)((int)&DAT_0095f7dc + *pcVar8 * 0x22) = 0;
        *(undefined2 *)((int)&DAT_0095f7dc + *pcVar8 * 0x22 + 2) = 0;
        *(undefined2 *)((int)&DAT_0095f7e0 + *pcVar8 * 0x22) = 0;
        *(undefined2 *)((int)&DAT_0095f7e0 + *pcVar8 * 0x22 + 2) = 0;
        *(undefined2 *)((int)&DAT_0095f7e4 + *pcVar8 * 0x22) = 0;
        *(undefined2 *)((int)&DAT_0095f7e4 + *pcVar8 * 0x22 + 2) = 0;
        *(undefined2 *)((int)&DAT_0095f7ec + *pcVar8 * 0x22) = 0x100;
        *(undefined2 *)((int)&DAT_0095f7ec + *pcVar8 * 0x22 + 2) = 0x100;
        *(undefined2 *)((int)&DAT_0095f7e8 + *pcVar8 * 0x22) = 0;
        *(undefined2 *)((int)&DAT_0095f7e8 + *pcVar8 * 0x22 + 2) = 0;
        (&DAT_0095f7f0)[*pcVar8 * 0x11] = 0;
        FUN_0043f650((int)*pcVar8,bVar1 & 3,1);
        FUN_0043f930((int)*pcVar8,bVar1 & 3,0,0,0,0,0,0,0x100,0x100,0,0,0);
        pcVar8 = pcVar8 + 1;
        uVar6 = uVar6 - 1;
      } while (uVar6 != 0);
    }
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 1;
  }
  return 0;
}
```

## Command 0x62
### Official name: objDisplay
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x62_objDisplay(int *param_1,undefined4 param_2,int *param_3,int *param_4)
{
  byte bVar1;
  int iVar2;
  uint *puVar3;
  char cVar4;
  undefined uVar5;
  undefined2 uVar6;
  int iVar7;
  uint uVar8;
  undefined2 extraout_var;
  undefined2 extraout_var_00;
  undefined2 *puVar9;
  int *piVar10;
  int *piVar11;
  
  iVar7 = *param_1;
  iVar2 = *param_4;
  if (iVar7 == 0) {
    *param_3 = 0;
    if ((&DAT_0097fb82)[iVar2] != '\0') {
      piVar11 = param_3 + 1;
      piVar10 = param_3 + 7;
      puVar9 = (undefined2 *)(&DAT_0097fb88 + iVar2);
      do {
        cVar4 = commandArgParser(puVar9[-1]);
        *(char *)piVar11 = cVar4;
        *(undefined2 *)(piVar10 + -4) = (&DAT_0095f7d4)[cVar4 * 0x11];
        uVar6 = commandArgParser(*puVar9);
        *(undefined2 *)piVar10 = uVar6;
        bVar1 = (&DAT_0097fb82)[iVar2];
        (&DAT_0095f7d4)[*(char *)piVar11 * 0x11] = uVar6;
        piVar11 = (int *)((int)piVar11 + 1);
        piVar10 = (int *)((int)piVar10 + 2);
        puVar9 = puVar9 + 2;
      } while ((-4 - (int)param_3) + (int)piVar11 < (int)(uint)bVar1);
    }
    puVar3 = DAT_0095d4d4;
    *DAT_0095d4d4 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar2];
    iVar7 = 0;
    *(ushort *)(puVar3 + 2) = (ushort)(byte)(&DAT_0097fb82)[iVar2];
    *(undefined2 *)((int)puVar3 + 10) = 0;
    if ((DAT_0095f6d0 == '\x02') || ((DAT_008e12ac & 0xa00) != 0)) {
      *(undefined2 *)((int)puVar3 + 10) = 1;
    }
    if ((&DAT_0097fb82)[iVar2] != '\0') {
      puVar9 = (undefined2 *)((int)puVar3 + 0xe);
      piVar11 = param_3 + 7;
      do {
        puVar9[-1] = (short)*(char *)((int)param_3 + iVar7 + 4);
        *puVar9 = *(undefined2 *)piVar11;
        *(undefined *)(puVar9 + 1) = 0;
        uVar8 = commandArgParser((short)(char)(&DAT_0097fb83)[iVar2]);
        if ((short)uVar8 == 0) {
          *(undefined *)(puVar9 + 9) = 2;
          uVar6 = extraout_var;
        }
        else {
          uVar5 = commandArgParser(uVar8 & 0xffff0000 |
                                   (uint)(ushort)(short)(char)(&DAT_0097fb83)[iVar2]);
          *(undefined *)(puVar9 + 9) = uVar5;
          uVar6 = extraout_var_00;
        }
        uVar5 = commandArgParser(CONCAT22(uVar6,(ushort)(byte)(&DAT_0097fb84)[iVar2]));
        *(undefined *)((int)puVar9 + 0x13) = uVar5;
        iVar7 = iVar7 + 1;
        piVar11 = (int *)((int)piVar11 + 2);
        puVar9 = puVar9 + 0xb;
      } while (iVar7 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    }
    FUN_0047f1e0(DAT_0095d53c,0);
    *param_1 = *param_1 + 1;
  }
  else if (iVar7 == 1) {
    iVar7 = FUN_0047f640(DAT_0095d534,1);
    if (iVar7 != 0) {
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
      return 2;
    }
  }
  else if ((iVar7 == 10) && (((byte)DAT_008e12b4 & 8) != 0)) {
    *param_1 = 1;
    *param_3 = *param_3 + 1;
    return 0;
  }
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x63
### Official name: objErase
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x63_objErase(int *param_1,undefined4 param_2,int *param_3,int *param_4)
{
  int iVar1;
  int iVar2;
  uint *puVar3;
  undefined uVar4;
  short sVar5;
  int iVar6;
  uint uVar7;
  undefined2 extraout_var;
  undefined2 extraout_var_00;
  undefined2 *puVar8;
  uint *puVar9;
  uint uVar10;
  
  iVar2 = *param_4;
  if (*param_1 == 0) {
    *param_3 = 0;
    sVar5 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar2));
    if (sVar5 == 0x4000) {
      uVar10 = 8;
      iVar6 = 0;
      do {
        *(char *)(iVar6 + 4 + (int)param_3) = (char)iVar6;
        iVar6 = iVar6 + 1;
      } while (iVar6 < 8);
    }
    else {
      uVar10 = (uint)(byte)(&DAT_0097fb82)[iVar2];
      iVar6 = 0;
      if (uVar10 != 0) {
        puVar8 = (undefined2 *)(&DAT_0097fb86 + iVar2);
        do {
          uVar4 = commandArgParser(*puVar8);
          *(undefined *)((int)param_3 + iVar6 + 4) = uVar4;
          iVar6 = iVar6 + 1;
          puVar8 = puVar8 + 1;
        } while (iVar6 < (int)uVar10);
      }
    }
    iVar6 = 0;
    if (uVar10 != 0) {
      do {
        iVar1 = iVar6 + 4;
        iVar6 = iVar6 + 1;
        (&DAT_0095f7d4)[*(char *)(iVar1 + (int)param_3) * 0x11] = 0xffff;
      } while (iVar6 < (int)uVar10);
    }
    puVar3 = DAT_0095d4d4;
    uVar7 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar2];
    iVar6 = 0;
    *DAT_0095d4d4 = uVar7;
    *(undefined2 *)((int)puVar3 + 10) = 0;
    if ((DAT_0095f6d0 == '\x02') || ((DAT_008e12ac & 0xa00) != 0)) {
      *(undefined2 *)((int)puVar3 + 10) = 1;
    }
    *(short *)(puVar3 + 2) = (short)uVar10;
    if ((short)uVar10 != 0) {
      puVar9 = puVar3 + 8;
      do {
        *(short *)(puVar9 + -5) = (short)*(char *)((int)param_3 + iVar6 + 4);
        uVar10 = commandArgParser(uVar7 & 0xffff0000 |
                                  (uint)(ushort)(short)(char)(&DAT_0097fb83)[iVar2]);
        if (((short)uVar10 == 0) ||
           (uVar10 = commandArgParser(CONCAT22(extraout_var,(short)(char)(&DAT_0097fb83)[iVar2])),
           (short)uVar10 == 3)) {
          *(undefined *)puVar9 = 2;
        }
        else {
          uVar10 = commandArgParser(CONCAT22(extraout_var_00,(short)(char)(&DAT_0097fb83)[iVar2]));
          *(char *)puVar9 = (char)uVar10;
        }
        uVar7 = commandArgParser(uVar10 & 0xffff0000 | (uint)(byte)(&DAT_0097fb84)[iVar2]);
        *(char *)((int)puVar9 + 1) = (char)uVar7;
        iVar6 = iVar6 + 1;
        puVar9 = (uint *)((int)puVar9 + 0x16);
      } while (iVar6 < (int)(uint)*(ushort *)(puVar3 + 2));
    }
    FUN_0047f1e0(DAT_0095d53c,0);
    *param_1 = *param_1 + 1;
  }
  else if ((*param_1 == 1) && (iVar6 = FUN_0047f640(DAT_0095d534,1), iVar6 != 0)) {
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 2;
  }
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x64
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x64(int *param_1,undefined4 param_2,int param_3,int *param_4)
{
  short *psVar1;
  byte bVar2;
  byte bVar3;
  int iVar4;
  char cVar5;
  short sVar6;
  short sVar7;
  short sVar8;
  undefined2 *puVar9;
  uint uVar10;
  char *pcVar11;
  short *psVar12;
  int iVar13;
  
  iVar4 = *param_4;
  bVar2 = (&DAT_0097fb83)[iVar4];
  bVar3 = (&DAT_0097fb82)[iVar4];
  uVar10 = bVar3 & 0xf;
  if (*param_1 != 0) {
    return 0;
  }
  if ((bVar2 & 0x30) == 0) {
    if ((bVar3 & 0xf) != 0) {
      pcVar11 = (char *)(param_3 + 4);
      psVar12 = (short *)(param_3 + 0x2c);
      puVar9 = (undefined2 *)(&DAT_0097fb86 + iVar4);
      param_1 = (int *)uVar10;
      do {
        cVar5 = commandArgParser(puVar9[-1]);
        *pcVar11 = cVar5;
        sVar6 = commandArgParser(*puVar9);
        *psVar12 = sVar6;
        sVar7 = commandArgParser(puVar9[1]);
        psVar12[1] = sVar7;
        sVar6 = (&DAT_0095f7d4)[*pcVar11 * 0x11];
        if (*psVar12 == 0x4000) {
          if (sVar6 < 0) {
            sVar8 = 0x140;
          }
          else {
            sVar8 = *(short *)((int)&DAT_0095f7dc + *pcVar11 * 0x22);
          }
          *psVar12 = sVar8;
        }
        if (sVar7 == 0x4000) {
          if (sVar6 < 0) {
            sVar6 = 0xe0;
          }
          else {
            sVar6 = *(short *)((int)&DAT_0095f7dc + *pcVar11 * 0x22 + 2);
          }
          psVar12[1] = sVar6;
        }
        *(short *)((int)&DAT_0095f7dc + *pcVar11 * 0x22) = *psVar12;
        cVar5 = *pcVar11;
        psVar1 = psVar12 + 1;
        puVar9 = puVar9 + 3;
        psVar12 = psVar12 + 2;
        pcVar11 = pcVar11 + 1;
        param_1 = (int *)((int)param_1 - 1);
        *(short *)((int)&DAT_0095f7dc + cVar5 * 0x22 + 2) = *psVar1;
      } while (param_1 != (int *)0x0);
    }
    iVar13 = 0;
    if ((bVar3 & 0xf) != 0) {
      puVar9 = (undefined2 *)(param_3 + 0x2c);
      do {
        FUN_0043f6a0((int)*(char *)(param_3 + 4 + iVar13),bVar2 & 3,*puVar9,puVar9[1]);
        iVar13 = iVar13 + 1;
        puVar9 = puVar9 + 2;
      } while (iVar13 < (int)uVar10);
    }
  }
  else if (((bVar2 & 0x30) == 0x10) && (bVar3 != 0)) {
    pcVar11 = (char *)(param_3 + 4);
    psVar12 = (short *)(&DAT_0097fb86 + iVar4);
    do {
      cVar5 = commandArgParser(psVar12[-1]);
      *pcVar11 = cVar5;
      if (*psVar12 != 0) {
        FUN_0044f060(*psVar12,(int)*(short *)((int)&DAT_0095f7dc + cVar5 * 0x22));
      }
      if (psVar12[1] != 0) {
        FUN_0044f060(psVar12[1],(int)*(short *)((int)&DAT_0095f7dc + *pcVar11 * 0x22 + 2));
      }
      pcVar11 = pcVar11 + 1;
      psVar12 = psVar12 + 3;
    } while ((int)(pcVar11 + (-4 - param_3)) < (int)(uint)(byte)(&DAT_0097fb82)[iVar4]);
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar4];
  return 1;
}
```

## Command 0x65
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
void command_0x65(undefined4 param_1,undefined4 param_2,undefined4 param_3,int *param_4)

{
  short sVar1;
  
  sVar1 = commandArgParser((uint)(&scriptBeginAddress_0x97fb80 + *param_4) & 0xffff0000 |
                           (uint)(ushort)(short)(char)(&DAT_0097fb83)[*param_4]);
  if (-1 < sVar1) {
    FUN_004565b0(param_3);
    return;
  }
  FUN_00456830(param_4);
  return;
}
```

## Command 0x66
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x66(int *param_1,undefined4 param_2,int param_3,int *param_4)
{
  short *psVar1;
  byte bVar2;
  byte bVar3;
  int iVar4;
  char cVar5;
  short sVar6;
  short sVar7;
  short sVar8;
  uint uVar9;
  undefined2 *puVar10;
  short *psVar11;
  int iVar12;
  char *pcVar13;
  
  iVar4 = *param_4;
  bVar2 = (&DAT_0097fb82)[iVar4];
  bVar3 = (&DAT_0097fb83)[iVar4];
  uVar9 = bVar2 & 0xf;
  if (*param_1 != 0) {
    return 0;
  }
  if ((bVar3 & 0x30) == 0) {
    if ((bVar2 & 0xf) != 0) {
      pcVar13 = (char *)(param_3 + 4);
      psVar11 = (short *)(param_3 + 0xc);
      puVar10 = (undefined2 *)(&DAT_0097fb86 + iVar4);
      param_1 = (int *)uVar9;
      do {
        cVar5 = commandArgParser(puVar10[-1]);
        *pcVar13 = cVar5;
        sVar6 = commandArgParser(*puVar10);
        *psVar11 = sVar6;
        sVar7 = commandArgParser(puVar10[1]);
        psVar11[1] = sVar7;
        sVar6 = (&DAT_0095f7d4)[*pcVar13 * 0x11];
        if (*psVar11 == 0x4000) {
          if (sVar6 < 0) {
            sVar8 = 0x100;
          }
          else {
            sVar8 = *(short *)((int)&DAT_0095f7ec + *pcVar13 * 0x22);
          }
          *psVar11 = sVar8;
        }
        if (sVar7 == 0x4000) {
          if (sVar6 < 0) {
            sVar6 = 0x100;
          }
          else {
            sVar6 = *(short *)((int)&DAT_0095f7ec + *pcVar13 * 0x22 + 2);
          }
          psVar11[1] = sVar6;
        }
        *(short *)((int)&DAT_0095f7ec + *pcVar13 * 0x22) = *psVar11;
        cVar5 = *pcVar13;
        psVar1 = psVar11 + 1;
        puVar10 = puVar10 + 3;
        psVar11 = psVar11 + 2;
        pcVar13 = pcVar13 + 1;
        param_1 = (int *)((int)param_1 - 1);
        *(short *)((int)&DAT_0095f7ec + cVar5 * 0x22 + 2) = *psVar1;
      } while (param_1 != (int *)0x0);
    }
    iVar12 = 0;
    if ((bVar2 & 0xf) != 0) {
      psVar11 = (short *)(param_3 + 0xc);
      do {
        FUN_0043f7e0((int)*(char *)(param_3 + 4 + iVar12),bVar3 & 3,(int)*psVar11,(int)psVar11[1]);
        iVar12 = iVar12 + 1;
        psVar11 = psVar11 + 2;
      } while (iVar12 < (int)uVar9);
    }
  }
  else if (((bVar3 & 0x30) == 0x10) && ((bVar2 & 0xf) != 0)) {
    pcVar13 = (char *)(param_3 + 4);
    psVar11 = (short *)(&DAT_0097fb86 + iVar4);
    do {
      cVar5 = commandArgParser(psVar11[-1]);
      *pcVar13 = cVar5;
      if (*psVar11 != 0) {
        FUN_0044f060(*psVar11,(int)*(short *)((int)&DAT_0095f7ec + cVar5 * 0x22));
      }
      if (psVar11[1] != 0) {
        FUN_0044f060(psVar11[1],(int)*(short *)((int)&DAT_0095f7ec + *pcVar13 * 0x22 + 2));
      }
      pcVar13 = pcVar13 + 1;
      psVar11 = psVar11 + 3;
      uVar9 = uVar9 - 1;
    } while (uVar9 != 0);
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar4];
  return 1;
}
```

## Command 0x67
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
void command_0x67(undefined4 param_1,undefined4 param_2,undefined4 param_3,int *param_4)

{
  short sVar1;
  
  sVar1 = commandArgParser((uint)(&scriptBeginAddress_0x97fb80 + *param_4) & 0xffff0000 |
                           (uint)(ushort)(short)(char)(&DAT_0097fb83)[*param_4]);
  if (-1 < sVar1) {
    FUN_00457230(param_3);
    return;
  }
  FUN_004574c0(param_4);
  return;
}
```

## Command 0x68
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x68(int *param_1,undefined4 param_2,int param_3,int *param_4)

{
  short *psVar1;
  byte bVar2;
  byte bVar3;
  int iVar4;
  char cVar5;
  short sVar6;
  short sVar7;
  short sVar8;
  uint uVar9;
  undefined2 *puVar10;
  short *psVar11;
  int iVar12;
  char *pcVar13;
  
  iVar4 = *param_4;
  bVar2 = (&DAT_0097fb82)[iVar4];
  bVar3 = (&DAT_0097fb83)[iVar4];
  uVar9 = bVar2 & 0xf;
  if (*param_1 != 0) {
    return 0;
  }
  if ((bVar3 & 0x30) == 0) {
    if ((bVar2 & 0xf) != 0) {
      pcVar13 = (char *)(param_3 + 4);
      psVar11 = (short *)(param_3 + 0xc);
      puVar10 = (undefined2 *)(&DAT_0097fb86 + iVar4);
      param_1 = (int *)uVar9;
      do {
        cVar5 = commandArgParser(puVar10[-1]);
        *pcVar13 = cVar5;
        sVar6 = commandArgParser(*puVar10);
        *psVar11 = sVar6;
        sVar7 = commandArgParser(puVar10[1]);
        psVar11[1] = sVar7;
        sVar6 = (&DAT_0095f7d4)[*pcVar13 * 0x11];
        if (*psVar11 == 0x4000) {
          if (sVar6 < 0) {
            sVar8 = 0;
          }
          else {
            sVar8 = *(short *)((int)&DAT_0095f7e8 + *pcVar13 * 0x22);
          }
          *psVar11 = sVar8;
        }
        if (sVar7 == 0x4000) {
          if (sVar6 < 0) {
            sVar6 = 0;
          }
          else {
            sVar6 = *(short *)((int)&DAT_0095f7e8 + *pcVar13 * 0x22 + 2);
          }
          psVar11[1] = sVar6;
        }
        *(short *)((int)&DAT_0095f7e8 + *pcVar13 * 0x22) = *psVar11;
        cVar5 = *pcVar13;
        psVar1 = psVar11 + 1;
        puVar10 = puVar10 + 3;
        psVar11 = psVar11 + 2;
        pcVar13 = pcVar13 + 1;
        param_1 = (int *)((int)param_1 - 1);
        *(short *)((int)&DAT_0095f7e8 + cVar5 * 0x22 + 2) = *psVar1;
      } while (param_1 != (int *)0x0);
    }
    iVar12 = 0;
    if ((bVar2 & 0xf) != 0) {
      psVar11 = (short *)(param_3 + 0xc);
      do {
        FUN_0043f860((int)*(char *)(param_3 + 4 + iVar12),bVar3 & 3,(int)*psVar11,(int)psVar11[1]);
        iVar12 = iVar12 + 1;
        psVar11 = psVar11 + 2;
      } while (iVar12 < (int)uVar9);
    }
  }
  else if (((bVar3 & 0x30) == 0x10) && ((bVar2 & 0xf) != 0)) {
    pcVar13 = (char *)(param_3 + 4);
    psVar11 = (short *)(&DAT_0097fb86 + iVar4);
    do {
      cVar5 = commandArgParser(psVar11[-1]);
      *pcVar13 = cVar5;
      if (*psVar11 != 0) {
        FUN_0044f060(*psVar11,(int)*(short *)((int)&DAT_0095f7e8 + cVar5 * 0x22));
      }
      if (psVar11[1] != 0) {
        FUN_0044f060(psVar11[1],(int)*(short *)((int)&DAT_0095f7e8 + *pcVar13 * 0x22 + 2));
      }
      pcVar13 = pcVar13 + 1;
      psVar11 = psVar11 + 3;
      uVar9 = uVar9 - 1;
    } while (uVar9 != 0);
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar4];
  return 1;
}
```

## Command 0x69
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
void command_0x69(undefined4 param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  short sVar1;
  
  sVar1 = commandArgParser((uint)(&scriptBeginAddress_0x97fb80 + *param_4) & 0xffff0000 |
                           (uint)(ushort)(short)(char)(&DAT_0097fb83)[*param_4]);
  if (-1 < sVar1) {
    FUN_00457790(param_3);
    return;
  }
  FUN_00457a20(param_4);
  return;
}
```

## Command 0x6A
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x6A(int *param_1,undefined4 param_2,int param_3,int *param_4)

{
  byte bVar1;
  byte bVar2;
  int iVar3;
  char cVar4;
  short sVar5;
  uint uVar6;
  undefined2 *puVar7;
  char *pcVar8;
  int iVar9;
  short *psVar10;
  
  iVar3 = *param_4;
  bVar1 = (&DAT_0097fb82)[iVar3];
  bVar2 = (&DAT_0097fb83)[iVar3];
  uVar6 = bVar1 & 0xf;
  if (*param_1 != 0) {
    return 0;
  }
  if ((bVar2 & 0x30) == 0) {
    if ((bVar1 & 0xf) != 0) {
      pcVar8 = (char *)(param_3 + 4);
      psVar10 = (short *)(param_3 + 0xc);
      puVar7 = (undefined2 *)(&DAT_0097fb86 + iVar3);
      param_1 = (int *)uVar6;
      do {
        cVar4 = commandArgParser(puVar7[-1]);
        *pcVar8 = cVar4;
        sVar5 = commandArgParser(*puVar7);
        *psVar10 = sVar5;
        if (sVar5 == 0x4000) {
          if ((short)(&DAT_0095f7d4)[*pcVar8 * 0x11] < 0) {
            sVar5 = 0;
          }
          else {
            sVar5 = (&DAT_0095f7f0)[*pcVar8 * 0x11];
          }
          *psVar10 = sVar5;
        }
        cVar4 = *pcVar8;
        sVar5 = *psVar10;
        psVar10 = psVar10 + 1;
        puVar7 = puVar7 + 2;
        pcVar8 = pcVar8 + 1;
        param_1 = (int *)((int)param_1 - 1);
        (&DAT_0095f7f0)[cVar4 * 0x11] = sVar5;
      } while (param_1 != (int *)0x0);
    }
    iVar9 = 0;
    if ((bVar1 & 0xf) != 0) {
      psVar10 = (short *)(param_3 + 0xc);
      do {
        FUN_0043f8e0((int)*(char *)(param_3 + 4 + iVar9),bVar2 & 3,(int)*psVar10);
        iVar9 = iVar9 + 1;
        psVar10 = psVar10 + 1;
      } while (iVar9 < (int)uVar6);
    }
  }
  else if (((bVar2 & 0x30) == 0x10) && (iVar9 = 0, (bVar1 & 0xf) != 0)) {
    psVar10 = (short *)(&DAT_0097fb86 + iVar3);
    do {
      cVar4 = commandArgParser(psVar10[-1]);
      *(char *)(param_3 + 4 + iVar9) = cVar4;
      if (*psVar10 != 0) {
        FUN_0044f060(*psVar10,(int)(short)(&DAT_0095f7f0)[cVar4 * 0x11]);
      }
      iVar9 = iVar9 + 1;
      psVar10 = psVar10 + 2;
    } while (iVar9 < (int)uVar6);
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar3];
  return 1;
```

## Command 0x6B
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
void command_0x6B(undefined4 param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  short sVar1;
  
  sVar1 = commandArgParser((uint)(&scriptBeginAddress_0x97fb80 + *param_4) & 0xffff0000 |
                           (uint)(ushort)(short)(char)(&DAT_0097fb83)[*param_4]);
  if (-1 < sVar1) {
    FUN_00457c60(param_3);
    return;
  }
  FUN_00457e60(param_3,param_4);
  return;
}
```

## Command 0x6C
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp

undefined4 command_0x6C(int *param_1,undefined4 param_2,int param_3,int *param_4)

{
  ushort *puVar1;
  byte bVar2;
  undefined2 uVar3;
  int iVar4;
  undefined uVar5;
  byte bVar6;
  char cVar7;
  short sVar8;
  ushort uVar9;
  int iVar10;
  undefined4 uVar11;
  int iVar12;
  undefined2 *puVar13;
  uint uVar14;
  char *pcVar15;
  ushort *puVar16;
  short *psVar17;
  
  iVar4 = *param_4;
  bVar2 = (&DAT_0097fb83)[iVar4];
  if (*param_1 != 0) {
    return 0;
  }
  switch(bVar2 & 0x30) {
  case 0:
  case 0x20:
  case 0x30:
    puVar13 = (undefined2 *)(&DAT_0097fb84 + iVar4);
    sVar8 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar4));
    if (sVar8 == 0x4000) {
      param_1 = (int *)0x8;
      iVar10 = 0;
      do {
        *(char *)(param_3 + 4 + iVar10) = (char)iVar10;
        iVar10 = iVar10 + 1;
      } while (iVar10 < 8);
    }
    else {
      param_1 = (int *)(uint)(byte)(&DAT_0097fb82)[iVar4];
      iVar10 = 0;
      if (param_1 != (int *)0x0) {
        do {
          uVar5 = commandArgParser(*puVar13);
          *(undefined *)(param_3 + 4 + iVar10) = uVar5;
          iVar10 = iVar10 + 1;
          puVar13 = puVar13 + 5;
        } while (iVar10 < (int)param_1);
      }
      FID_conflict:_wprintf("ObjCol Cid:%d\n",(int)*(char *)(iVar10 + 4 + param_3));
    }
    bVar6 = (&DAT_0097fb83)[iVar4] & 0x30;
    if (((&DAT_0097fb83)[iVar4] & 0x30) == 0) {
      if (param_1 == (int *)0x0) break;
      pcVar15 = (char *)(param_3 + 4);
      puVar16 = (ushort *)(param_3 + 0xe);
      puVar13 = (undefined2 *)(&DAT_0097fb88 + iVar4);
      uVar14 = (uint)param_1;
      do {
        sVar8 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar4));
        if (sVar8 == 0x4000) {
          uVar9 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar4));
          puVar16[-1] = uVar9;
          uVar9 = commandArgParser(*(undefined2 *)(&DAT_0097fb88 + iVar4));
          *puVar16 = uVar9;
          uVar9 = commandArgParser(*(undefined2 *)(&DAT_0097fb8a + iVar4));
          puVar16[1] = uVar9;
          uVar3 = *(undefined2 *)(&DAT_0097fb8c + iVar4);
        }
        else {
          uVar9 = commandArgParser(puVar13[-1]);
          puVar16[-1] = uVar9;
          uVar9 = commandArgParser(*puVar13);
          *puVar16 = uVar9;
          uVar9 = commandArgParser(puVar13[1]);
          puVar16[1] = uVar9;
          uVar3 = puVar13[2];
        }
        uVar9 = commandArgParser(uVar3);
        puVar16[2] = uVar9;
        if (puVar16[-1] == 0x4000) {
          puVar16[-1] = (ushort)*(byte *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22);
        }
        if (*puVar16 == 0x4000) {
          *puVar16 = (ushort)*(byte *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22 + 1);
        }
        if (puVar16[1] == 0x4000) {
          puVar16[1] = (ushort)*(byte *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22 + 2);
        }
        if (puVar16[2] == 0x4000) {
          puVar16[2] = (ushort)*(byte *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22 + 3);
        }
        *(undefined *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22) = *(undefined *)(puVar16 + -1);
        *(undefined *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22 + 1) = *(undefined *)puVar16;
        *(undefined *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22 + 2) = *(undefined *)(puVar16 + 1);
        cVar7 = *pcVar15;
        puVar1 = puVar16 + 2;
        puVar13 = puVar13 + 5;
        puVar16 = puVar16 + 4;
        pcVar15 = pcVar15 + 1;
        uVar14 = uVar14 - 1;
        *(undefined *)((int)&DAT_0095f7f2 + cVar7 * 0x22 + 3) = *(undefined *)puVar1;
      } while (uVar14 != 0);
    }
    else if (bVar6 == 0x20) {
      if (param_1 == (int *)0x0) break;
      pcVar15 = (char *)(param_3 + 4);
      uVar14 = (uint)param_1;
      psVar17 = (short *)(&DAT_0097fb86 + iVar4);
      do {
        sVar8 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar4));
        if (sVar8 == 0x4000) {
          *(undefined4 *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22) =
               *(undefined4 *)(DAT_0095fb18 + *(short *)(&DAT_0097fb86 + iVar4) * 4);
        }
        else {
          *(undefined4 *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22) =
               *(undefined4 *)(DAT_0095fb18 + *psVar17 * 4);
        }
        psVar17 = psVar17 + 2;
        pcVar15 = pcVar15 + 1;
        uVar14 = uVar14 - 1;
      } while (uVar14 != 0);
    }
    else if (bVar6 == 0x30) {
      if (param_1 == (int *)0x0) break;
      pcVar15 = (char *)(param_3 + 4);
      uVar14 = (uint)param_1;
      puVar13 = (undefined2 *)(&DAT_0097fb86 + iVar4);
      do {
        sVar8 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar4));
        if (sVar8 == 0x4000) {
          uVar11 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar4));
          sVar8 = FUN_00452ea0(uVar11);
          *(undefined4 *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22) =
               *(undefined4 *)(DAT_0095fb18 + sVar8 * 4);
        }
        else {
          uVar11 = commandArgParser(*puVar13);
          sVar8 = FUN_00452ea0(uVar11);
          *(undefined4 *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22) =
               *(undefined4 *)(DAT_0095fb18 + sVar8 * 4);
        }
        puVar13 = puVar13 + 2;
        pcVar15 = pcVar15 + 1;
        uVar14 = uVar14 - 1;
      } while (uVar14 != 0);
    }
    if (param_1 != (int *)0x0) {
      pcVar15 = (char *)(param_3 + 4);
      do {
        iVar12 = (int)*pcVar15;
        iVar10 = iVar12 * 0x22;
        FUN_0043fc20(iVar12,bVar2 & 3,*(undefined *)((int)&DAT_0095f7f2 + iVar10),
                     *(undefined *)((int)&DAT_0095f7f2 + iVar10 + 1),
                     *(undefined *)((int)&DAT_0095f7f2 + iVar10 + 2),
                     *(undefined *)((int)&DAT_0095f7f2 + iVar12 * 0x22 + 3));
        pcVar15 = pcVar15 + 1;
        param_1 = (int *)((int)param_1 - 1);
      } while (param_1 != (int *)0x0);
    }
    break;
  case 0x10:
    if ((&DAT_0097fb82)[iVar4] != '\0') {
      pcVar15 = (char *)(param_3 + 4);
      psVar17 = (short *)(&DAT_0097fb86 + iVar4);
      do {
        cVar7 = commandArgParser(psVar17[-1]);
        *pcVar15 = cVar7;
        if (*psVar17 != 0) {
          FUN_0044f060(*psVar17,*(undefined *)((int)&DAT_0095f7f2 + cVar7 * 0x22));
        }
        if (psVar17[1] != 0) {
          FUN_0044f060(psVar17[1],*(undefined *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22 + 1));
        }
        if (psVar17[2] != 0) {
          FUN_0044f060(psVar17[2],*(undefined *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22 + 2));
        }
        if (psVar17[3] != 0) {
          FUN_0044f060(psVar17[3],*(undefined *)((int)&DAT_0095f7f2 + *pcVar15 * 0x22 + 3));
        }
        pcVar15 = pcVar15 + 1;
        psVar17 = psVar17 + 5;
      } while ((int)(pcVar15 + (-4 - param_3)) < (int)(uint)(byte)(&DAT_0097fb82)[iVar4]);
    }
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar4];
  return 1;
}
```

## Command 0x6D
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
void command_0x6D(undefined4 param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  short sVar1;
  
  sVar1 = commandArgParser((uint)(&scriptBeginAddress_0x97fb80 + *param_4) & 0xffff0000 |
                           (uint)(ushort)(short)(char)(&DAT_0097fb83)[*param_4]);
  if (-1 < sVar1) {
    FUN_00458440(param_3);
    return;
  }
  FUN_004587c0(param_4);
  return;
}
```

## Command 0x6E
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x6E(int *param_1,undefined4 param_2,int param_3,int *param_4)
{
  short *psVar1;
  byte bVar2;
  byte bVar3;
  int iVar4;
  bool bVar5;
  char cVar6;
  short sVar7;
  short sVar8;
  uint uVar9;
  short *psVar10;
  undefined2 *puVar11;
  char *pcVar12;
  int iVar13;
  
  iVar4 = *param_4;
  bVar2 = (&DAT_0097fb82)[iVar4];
  bVar3 = (&DAT_0097fb83)[iVar4];
  uVar9 = bVar2 & 0xf;
  if (*param_1 != 0) {
    return 0;
  }
  if ((bVar3 & 0x30) == 0) {
    if ((bVar2 & 0xf) != 0) {
      pcVar12 = (char *)(param_3 + 4);
      psVar10 = (short *)(param_3 + 0xe);
      puVar11 = (undefined2 *)(&DAT_0097fb86 + iVar4);
      param_1 = (int *)uVar9;
      do {
        cVar6 = commandArgParser(puVar11[-1]);
        *pcVar12 = cVar6;
        sVar7 = commandArgParser(*puVar11);
        psVar10[-1] = sVar7;
        sVar7 = commandArgParser(puVar11[1]);
        *psVar10 = sVar7;
        sVar7 = commandArgParser(puVar11[2]);
        psVar10[1] = sVar7;
        sVar7 = commandArgParser(puVar11[3]);
        psVar10[2] = sVar7;
        bVar5 = (short)(&DAT_0095f7d4)[*pcVar12 * 0x11] < 0;
        if (psVar10[-1] == 0x4000) {
          if (bVar5) {
            sVar8 = 0;
          }
          else {
            sVar8 = *(short *)((int)&DAT_0095f7e0 + *pcVar12 * 0x22);
          }
          psVar10[-1] = sVar8;
        }
        if (*psVar10 == 0x4000) {
          if (bVar5) {
            sVar8 = 0;
          }
          else {
            sVar8 = *(short *)((int)&DAT_0095f7e0 + *pcVar12 * 0x22 + 2);
          }
          *psVar10 = sVar8;
        }
        if (psVar10[1] == 0x4000) {
          if (bVar5) {
            sVar8 = 0;
          }
          else {
            sVar8 = *(short *)((int)&DAT_0095f7e4 + *pcVar12 * 0x22);
          }
          psVar10[1] = sVar8;
        }
        if (sVar7 == 0x4000) {
          if (bVar5) {
            sVar7 = 0;
          }
          else {
            sVar7 = *(short *)((int)&DAT_0095f7e4 + *pcVar12 * 0x22 + 2);
          }
          psVar10[2] = sVar7;
        }
        *(short *)((int)&DAT_0095f7e0 + *pcVar12 * 0x22) = psVar10[-1];
        *(short *)((int)&DAT_0095f7e0 + *pcVar12 * 0x22 + 2) = *psVar10;
        *(short *)((int)&DAT_0095f7e4 + *pcVar12 * 0x22) = psVar10[1];
        cVar6 = *pcVar12;
        psVar1 = psVar10 + 2;
        puVar11 = puVar11 + 5;
        psVar10 = psVar10 + 4;
        pcVar12 = pcVar12 + 1;
        param_1 = (int *)((int)param_1 - 1);
        *(short *)((int)&DAT_0095f7e4 + cVar6 * 0x22 + 2) = *psVar1;
      } while (param_1 != (int *)0x0);
    }
    iVar13 = 0;
    if ((bVar2 & 0xf) != 0) {
      puVar11 = (undefined2 *)(param_3 + 0x10);
      do {
        FUN_0043f720((int)*(char *)(param_3 + 4 + iVar13),bVar3 & 3,puVar11[-2],puVar11[-1],*puVar11
                     ,puVar11[1]);
        iVar13 = iVar13 + 1;
        puVar11 = puVar11 + 4;
      } while (iVar13 < (int)uVar9);
    }
  }
  else if (((bVar3 & 0x30) == 0x10) && ((bVar2 & 0xf) != 0)) {
    pcVar12 = (char *)(param_3 + 4);
    psVar10 = (short *)(&DAT_0097fb86 + iVar4);
    do {
      cVar6 = commandArgParser(psVar10[-1]);
      *pcVar12 = cVar6;
      if (*psVar10 != 0) {
        FUN_0044f060(*psVar10,(int)*(short *)((int)&DAT_0095f7e0 + cVar6 * 0x22));
      }
      if (psVar10[1] != 0) {
        FUN_0044f060(psVar10[1],(int)*(short *)((int)&DAT_0095f7e0 + *pcVar12 * 0x22 + 2));
      }
      if (psVar10[2] != 0) {
        FUN_0044f060(psVar10[2],(int)*(short *)((int)&DAT_0095f7e4 + *pcVar12 * 0x22));
      }
      if (psVar10[3] != 0) {
        FUN_0044f060(psVar10[3],(int)*(short *)((int)&DAT_0095f7e4 + *pcVar12 * 0x22 + 2));
      }
      pcVar12 = pcVar12 + 1;
      psVar10 = psVar10 + 5;
      uVar9 = uVar9 - 1;
    } while (uVar9 != 0);
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar4];
  return 1;
}
```

## Command 0x6F
### Official name: (N/A)
### My guess: (N/A)

### Code
```cpp
void command_0x6F(undefined4 param_1,undefined4 param_2,undefined4 param_3,int *param_4)

{
  short sVar1;
  
  sVar1 = commandArgParser((uint)(&scriptBeginAddress_0x97fb80 + *param_4) & 0xffff0000 |
                           (uint)(ushort)(short)(char)(&DAT_0097fb83)[*param_4]);
  if (-1 < sVar1) {
    FUN_00456be0(param_3);
    return;
  }
  FUN_00456f20(param_4);
  return;
}
```

## Command 0x70
### Official name: objNo
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x70_objNo(int *param_1,undefined4 param_2,int param_3,int *param_4)

{
  ushort uVar1;
  int iVar2;
  char cVar3;
  uint uVar4;
  ushort *puVar5;
  int iVar6;
  
  iVar2 = *param_4;
  if (*param_1 == 0) {
    if ((((&DAT_0097fb83)[iVar2] & 0x30) == 0x10) && (iVar6 = 0, (&DAT_0097fb82)[iVar2] != '\0')) {
      puVar5 = (ushort *)(&DAT_0097fb86 + iVar2);
      do {
        cVar3 = commandArgParser(puVar5[-1]);
        *(char *)(iVar6 + 4 + param_3) = cVar3;
        uVar1 = *puVar5;
        if (uVar1 != 0) {
          uVar4 = (uint)uVar1;
          if ((ushort)(uVar1 + 0x8000) < 0x1000) {
            if ((uVar4 & 0xfff) < 0x800) {
              (&DAT_0095d860)[uVar4 & 0x7ff] = (&DAT_0095f7d4)[cVar3 * 0x11];
            }
            else {
              (&DAT_0095d560)[uVar4 & 0x7ff] = (byte)(&DAT_0095f7d4)[cVar3 * 0x11] & 1;
            }
          }
        }
        iVar6 = iVar6 + 1;
        puVar5 = puVar5 + 2;
      } while (iVar6 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    }
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 1;
  }
  return 0;
}
```

## Command 0x71
### Official name: objOn
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x71_objOn(int *param_1,undefined4 param_2,uint param_3,int *param_4)
{
  byte bVar1;
  int iVar2;
  char cVar3;
  undefined uVar4;
  short sVar5;
  undefined2 uVar6;
  uint uVar7;
  int iVar8;
  int iVar9;
  undefined2 *puVar10;
  undefined2 *puVar11;
  short *psVar12;
  char *pcVar13;
  
  iVar8 = param_3;
  iVar2 = *param_4;
  bVar1 = (&DAT_0097fb83)[iVar2];
  if (*param_1 == 0) {
    if ((bVar1 & 0x30) == 0) {
      sVar5 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
      if (sVar5 == 0x4000) {
        param_3 = 8;
        iVar9 = 0;
        puVar10 = (undefined2 *)(iVar8 + 0xc);
        do {
          *(char *)(iVar9 + 4 + iVar8) = (char)iVar9;
          uVar6 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar2));
          *puVar10 = uVar6;
          iVar9 = iVar9 + 1;
          puVar10 = puVar10 + 1;
          uVar7 = param_3;
        } while (iVar9 < 8);
      }
      else {
        uVar7 = (uint)(byte)(&DAT_0097fb82)[iVar2];
        iVar9 = 0;
        if (uVar7 != 0) {
          puVar10 = (undefined2 *)(param_3 + 0xc);
          puVar11 = (undefined2 *)(&DAT_0097fb86 + iVar2);
          do {
            uVar4 = commandArgParser(puVar11[-1]);
            *(undefined *)(iVar9 + 4 + param_3) = uVar4;
            uVar6 = commandArgParser(*puVar11);
            *puVar10 = uVar6;
            iVar9 = iVar9 + 1;
            puVar10 = puVar10 + 1;
            puVar11 = puVar11 + 2;
          } while (iVar9 < (int)uVar7);
        }
      }
      param_3 = uVar7;
      if (param_3 != 0) {
        pcVar13 = (char *)(iVar8 + 4);
        puVar10 = (undefined2 *)(iVar8 + 0xc);
        do {
          (&DAT_0095f7d8)[*pcVar13 * 0x22] = *(undefined *)puVar10;
          FUN_0043f650((int)*pcVar13,bVar1 & 3,*puVar10);
          puVar10 = puVar10 + 1;
          pcVar13 = pcVar13 + 1;
          param_3 = param_3 - 1;
        } while (param_3 != 0);
      }
    }
    else if (((bVar1 & 0x30) == 0x10) && (iVar8 = 0, (&DAT_0097fb82)[iVar2] != '\0')) {
      psVar12 = (short *)(&DAT_0097fb86 + iVar2);
      do {
        cVar3 = commandArgParser(psVar12[-1]);
        *(char *)(iVar8 + 4 + param_3) = cVar3;
        if (*psVar12 != 0) {
          FUN_0044f060(*psVar12,(int)(char)(&DAT_0095f7d8)[cVar3 * 0x22]);
        }
        iVar8 = iVar8 + 1;
        psVar12 = psVar12 + 2;
      } while (iVar8 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    }
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 1;
  }
  return 0;
}
```

## Command 0x72
### Official name: objPri
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x72_objPri(int *param_1,undefined4 param_2,uint param_3,int *param_4)
{
  byte bVar1;
  int iVar2;
  char cVar3;
  undefined uVar4;
  short sVar5;
  undefined2 uVar6;
  uint uVar7;
  int iVar8;
  int iVar9;
  undefined2 *puVar10;
  undefined2 *puVar11;
  short *psVar12;
  char *pcVar13;
  
  iVar8 = param_3;
  iVar2 = *param_4;
  bVar1 = (&DAT_0097fb83)[iVar2];
  if (*param_1 == 0) {
    if ((bVar1 & 0x30) == 0) {
      sVar5 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
      if (sVar5 == 0x4000) {
        param_3 = 8;
        iVar9 = 0;
        puVar10 = (undefined2 *)(iVar8 + 0xc);
        do {
          *(char *)(iVar9 + 4 + iVar8) = (char)iVar9;
          uVar6 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar2));
          *puVar10 = uVar6;
          iVar9 = iVar9 + 1;
          puVar10 = puVar10 + 1;
          uVar7 = param_3;
        } while (iVar9 < 8);
      }
      else {
        uVar7 = (uint)(byte)(&DAT_0097fb82)[iVar2];
        iVar9 = 0;
        if (uVar7 != 0) {
          puVar10 = (undefined2 *)(param_3 + 0xc);
          puVar11 = (undefined2 *)(&DAT_0097fb86 + iVar2);
          do {
            uVar4 = commandArgParser(puVar11[-1]);
            *(undefined *)(iVar9 + 4 + param_3) = uVar4;
            uVar6 = commandArgParser(*puVar11);
            *puVar10 = uVar6;
            iVar9 = iVar9 + 1;
            puVar10 = puVar10 + 1;
            puVar11 = puVar11 + 2;
          } while (iVar9 < (int)uVar7);
        }
      }
      param_3 = uVar7;
      if (param_3 != 0) {
        pcVar13 = (char *)(iVar8 + 4);
        puVar10 = (undefined2 *)(iVar8 + 0xc);
        do {
          (&DAT_0095f7d9)[*pcVar13 * 0x22] = *(undefined *)puVar10;
          FUN_0043fd10((int)*pcVar13,bVar1 & 3,*puVar10);
          puVar10 = puVar10 + 1;
          pcVar13 = pcVar13 + 1;
          param_3 = param_3 - 1;
        } while (param_3 != 0);
      }
    }
    else if (((bVar1 & 0x30) == 0x10) && (iVar8 = 0, (&DAT_0097fb82)[iVar2] != '\0')) {
      psVar12 = (short *)(&DAT_0097fb86 + iVar2);
      do {
        cVar3 = commandArgParser(psVar12[-1]);
        *(char *)(iVar8 + 4 + param_3) = cVar3;
        if (*psVar12 != 0) {
          FUN_0044f060(*psVar12,(int)(char)(&DAT_0095f7d9)[cVar3 * 0x22]);
        }
        iVar8 = iVar8 + 1;
        psVar12 = psVar12 + 2;
      } while (iVar8 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    }
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 1;
  }
  return 0;
}
```

## Command 0x73
### Official name: objAnimate
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x73_objAnimate(int *param_1,undefined4 param_2,int param_3,int *param_4)

{
  byte bVar1;
  int iVar2;
  undefined uVar3;
  short sVar4;
  undefined2 uVar5;
  int iVar6;
  undefined2 *puVar7;
  undefined2 *puVar8;
  
  iVar2 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  if (((&DAT_0097fb83)[iVar2] & 0x30) == 0) {
    sVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
    if (sVar4 == 0x4000) {
      iVar6 = 0;
      puVar8 = (undefined2 *)(param_3 + 0x1c);
      do {
        *(char *)(param_3 + 4 + iVar6) = (char)iVar6;
        uVar5 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar2));
        puVar8[-8] = uVar5;
        uVar5 = commandArgParser(*(undefined2 *)(&DAT_0097fb88 + iVar2));
        *puVar8 = uVar5;
        iVar6 = iVar6 + 1;
        puVar8 = puVar8 + 1;
      } while (iVar6 < 8);
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
      return 1;
    }
    bVar1 = (&DAT_0097fb82)[iVar2];
    iVar6 = 0;
    if (bVar1 != 0) {
      puVar7 = (undefined2 *)(param_3 + 0x1c);
      puVar8 = (undefined2 *)(&DAT_0097fb86 + iVar2);
      do {
        uVar3 = commandArgParser(puVar8[-1]);
        *(undefined *)(param_3 + 4 + iVar6) = uVar3;
        uVar5 = commandArgParser(*puVar8);
        puVar7[-8] = uVar5;
        uVar5 = commandArgParser(puVar8[1]);
        *puVar7 = uVar5;
        iVar6 = iVar6 + 1;
        puVar7 = puVar7 + 1;
        puVar8 = puVar8 + 3;
      } while (iVar6 < (int)(uint)bVar1);
    }
  }
  else if ((((&DAT_0097fb83)[iVar2] & 0x30) == 0x10) && (iVar6 = 0, (&DAT_0097fb82)[iVar2] != '\0'))
  {
    puVar8 = (undefined2 *)(&DAT_0097fb84 + iVar2);
    do {
      uVar3 = commandArgParser(*puVar8);
      *(undefined *)(param_3 + 4 + iVar6) = uVar3;
      iVar6 = iVar6 + 1;
      puVar8 = puVar8 + 3;
    } while (iVar6 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 1;
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
  return 1;
}
```

## Command 0x74
### Official name: objSort
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x74_objSort(int *param_1,undefined4 param_2,int *param_3,int *param_4)
{
  char cVar1;
  int iVar2;
  int iVar3;
  int iVar4;
  
  iVar2 = *param_4;
  if (*param_1 != 0) {
    *param_3 = *param_3 + 1;
    return 0;
  }
  iVar4 = (byte)(&scriptCommandLength_0x0097fb81)[iVar2] - 2;
  if (8 < iVar4) {
    iVar4 = 8;
  }
  iVar3 = 0;
  if (0 < iVar4) {
    do {
      cVar1 = (&DAT_0097fb82)[iVar3 + iVar2];
      if (cVar1 < '\0') break;
      (&DAT_0095f7da)[cVar1 * 0x22] = (char)iVar3;
      FUN_0043fd60((int)cVar1,2,iVar3);
      iVar3 = iVar3 + 1;
    } while (iVar3 < iVar4);
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
  return 2;
}
```

## Command 0x75
### Official name: objSort
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x75_objSwap(int *param_1,undefined4 param_2,int param_3,int *param_4)

{
  short sVar1;
  int iVar2;
  undefined2 uVar3;
  short sVar4;
  int iVar5;
  undefined4 *puVar6;
  undefined4 *puVar7;
  undefined4 local_24 [9];
  
  iVar2 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  uVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb82 + iVar2));
  *(undefined2 *)(param_3 + 4) = uVar3;
  sVar4 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
  sVar1 = *(short *)(param_3 + 4);
  *(short *)(param_3 + 6) = sVar4;
  puVar6 = (undefined4 *)(&DAT_0095f7d4 + sVar1 * 0x11);
  puVar7 = local_24;
  for (iVar5 = 8; iVar5 != 0; iVar5 = iVar5 + -1) {
    *puVar7 = *puVar6;
    puVar6 = puVar6 + 1;
    puVar7 = puVar7 + 1;
  }
  *(undefined2 *)puVar7 = *(undefined2 *)puVar6;
  puVar6 = (undefined4 *)(&DAT_0095f7d4 + sVar4 * 0x11);
  puVar7 = (undefined4 *)(&DAT_0095f7d4 + sVar1 * 0x11);
  for (iVar5 = 8; iVar5 != 0; iVar5 = iVar5 + -1) {
    *puVar7 = *puVar6;
    puVar6 = puVar6 + 1;
    puVar7 = puVar7 + 1;
  }
  *(undefined2 *)puVar7 = *(undefined2 *)puVar6;
  puVar6 = local_24;
  puVar7 = (undefined4 *)(&DAT_0095f7d4 + *(short *)(param_3 + 6) * 0x11);
  for (iVar5 = 8; iVar5 != 0; iVar5 = iVar5 + -1) {
    *puVar7 = *puVar6;
    puVar6 = puVar6 + 1;
    puVar7 = puVar7 + 1;
  }
  *(undefined2 *)puVar7 = *(undefined2 *)puVar6;
  FUN_0043f590((int)*(short *)(param_3 + 4),(int)*(short *)(param_3 + 6));
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
  return 1;
}
```

## Command 0x80
### Official name: faceInit
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x80_faceInit(int *param_1,undefined4 param_2,int param_3,int *param_4)
{
  int iVar1;
  char cVar2;
  short sVar3;
  int iVar4;
  uint uVar5;
  char *pcVar6;
  undefined2 *puVar7;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  puVar7 = (undefined2 *)(&DAT_0097fb84 + iVar1);
  sVar3 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar1));
  if (sVar3 != 0x4000) {
    uVar5 = (uint)(byte)(&DAT_0097fb82)[iVar1];
    if (uVar5 != 0) {
      pcVar6 = (char *)(param_3 + 4);
      do {
        cVar2 = commandArgParser(*puVar7);
        *pcVar6 = cVar2;
        (&DAT_0095f8e8)[cVar2 * 0xe] = 1;
        *(undefined2 *)((int)&DAT_0095f8ec + *pcVar6 * 0xe) = 0;
        cVar2 = *pcVar6;
        puVar7 = puVar7 + 1;
        pcVar6 = pcVar6 + 1;
        uVar5 = uVar5 - 1;
        *(undefined2 *)((int)&DAT_0095f8ec + cVar2 * 0xe + 2) = 0;
      } while (uVar5 != 0);
    }
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
    return 1;
  }
  iVar4 = 0;
  do {
    *(char *)(param_3 + 4 + iVar4) = (char)iVar4;
    (&DAT_0095f8e8)[(char)iVar4 * 0xe] = 1;
    *(undefined2 *)((int)&DAT_0095f8ec + *(char *)(param_3 + 4 + iVar4) * 0xe) = 0;
    pcVar6 = (char *)(param_3 + 4 + iVar4);
    iVar4 = iVar4 + 1;
    *(undefined2 *)((int)&DAT_0095f8ec + *pcVar6 * 0xe + 2) = 0;
  } while (iVar4 < 2);
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```

## Command 0x82
### Official name: faceDisplay
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x82_faceDisplay(int *param_1,undefined4 param_2,int *param_3,int *param_4)

{
  byte bVar1;
  int iVar2;
  uint *puVar3;
  char cVar4;
  undefined uVar5;
  undefined2 uVar6;
  int iVar7;
  uint uVar8;
  undefined2 extraout_var;
  undefined2 extraout_var_00;
  undefined2 *puVar9;
  undefined2 *puVar10;
  short *psVar11;
  int *piVar12;
  short *psVar13;
  
  iVar7 = *param_1;
  iVar2 = *param_4;
  if (iVar7 == 0) {
    *param_3 = 0;
    param_4._0_1_ = 0;
    if ((DAT_0095f6d0 == '\x02') && ((DAT_042b52ea != '\0' || (DAT_042b52e9 != '\0')))) {
      param_4._0_1_ = 1;
    }
    if ((&DAT_0097fb82)[iVar2] != '\0') {
      piVar12 = param_3 + 1;
      puVar10 = (undefined2 *)((int)param_3 + 10);
      puVar9 = (undefined2 *)(&DAT_0097fb88 + iVar2);
      do {
        cVar4 = commandArgParser(puVar9[-1]);
        *(char *)piVar12 = cVar4;
        puVar10[-2] = (&DAT_0095f8e4)[cVar4 * 7];
        uVar6 = commandArgParser(*puVar9);
        *puVar10 = uVar6;
        bVar1 = (&DAT_0097fb82)[iVar2];
        (&DAT_0095f8e4)[*(char *)piVar12 * 7] = uVar6;
        piVar12 = (int *)((int)piVar12 + 1);
        puVar10 = puVar10 + 1;
        puVar9 = puVar9 + 2;
      } while ((-4 - (int)param_3) + (int)piVar12 < (int)(uint)bVar1);
    }
    puVar3 = DAT_0095d4d4;
    *DAT_0095d4d4 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar2];
    iVar7 = 0;
    *(ushort *)(puVar3 + 2) = (ushort)(byte)(&DAT_0097fb82)[iVar2];
    *(undefined2 *)((int)puVar3 + 10) = 0;
    if ((DAT_0095f6d0 == '\x02') || ((DAT_008e12ac & 0xa00) != 0)) {
      *(undefined2 *)((int)puVar3 + 10) = 1;
    }
    if ((&DAT_0097fb82)[iVar2] != '\0') {
      psVar11 = (short *)((int)param_3 + 10);
      psVar13 = (short *)((int)puVar3 + 0xe);
      do {
        cVar4 = *(char *)((int)param_3 + iVar7 + 4);
        psVar13[-1] = (short)cVar4;
        *psVar13 = *psVar11;
        *(undefined *)(psVar13 + 1) = param_4._0_1_;
        uVar8 = commandArgParser(CONCAT22((undefined2)(cVar4 >> 7),
                                          (short)(char)(&DAT_0097fb83)[iVar2]));
        if ((short)uVar8 == 0) {
          uVar5 = FUN_00452d50((int)psVar11[-2],(int)*psVar11);
          uVar6 = extraout_var;
        }
        else {
          uVar5 = commandArgParser(uVar8 & 0xffff0000 |
                                   (uint)(ushort)(short)(char)(&DAT_0097fb83)[iVar2]);
          uVar6 = extraout_var_00;
        }
        *(undefined *)((int)psVar13 + 3) = uVar5;
        uVar5 = commandArgParser(CONCAT22(uVar6,(ushort)(byte)(&DAT_0097fb84)[iVar2]));
        *(undefined *)(psVar13 + 2) = uVar5;
        iVar7 = iVar7 + 1;
        psVar11 = psVar11 + 1;
        psVar13 = psVar13 + 4;
      } while (iVar7 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    }
    FUN_0047f1e0(DAT_0095d53c,0);
    *param_1 = *param_1 + 1;
  }
  else if (iVar7 == 1) {
    iVar7 = FUN_0047f640(DAT_0095d530,1);
    if (iVar7 != 0) {
      *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
      return 2;
    }
  }
  else if ((iVar7 == 10) && (((byte)DAT_008e12b4 & 8) != 0)) {
    *param_1 = 1;
    *param_3 = *param_3 + 1;
    return 0;
  }
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x83
### Official name: faceErase
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x83_faceErase(int *param_1,undefined4 param_2,int *param_3,int *param_4)

{
  byte bVar1;
  int iVar2;
  uint *puVar3;
  char cVar4;
  undefined uVar5;
  short sVar6;
  int iVar7;
  uint uVar8;
  undefined2 extraout_var;
  undefined2 extraout_var_00;
  undefined2 extraout_var_01;
  undefined2 extraout_var_02;
  undefined2 extraout_var_03;
  undefined2 uVar9;
  uint extraout_EDX;
  undefined2 extraout_var_04;
  undefined2 *puVar10;
  undefined *puVar11;
  undefined8 uVar12;
  
  iVar2 = *param_4;
  if (*param_1 == 0) {
    *param_3 = 0;
    puVar10 = (undefined2 *)(&DAT_0097fb86 + iVar2);
    sVar6 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar2));
    if (sVar6 == 0x4000) {
      iVar7 = 0;
      do {
        cVar4 = (char)iVar7;
        *(char *)((int)param_3 + iVar7 + 4) = cVar4;
        iVar7 = iVar7 + 1;
        (&DAT_0095f8e4)[cVar4 * 7] = 0xffff;
      } while (iVar7 < 2);
    }
    else {
      iVar7 = 0;
      if ((&DAT_0097fb82)[iVar2] != '\0') {
        do {
          cVar4 = commandArgParser(*puVar10);
          *(char *)((int)param_3 + iVar7 + 4) = cVar4;
          bVar1 = (&DAT_0097fb82)[iVar2];
          iVar7 = iVar7 + 1;
          puVar10 = puVar10 + 1;
          (&DAT_0095f8e4)[cVar4 * 7] = 0xffff;
        } while (iVar7 < (int)(uint)bVar1);
      }
    }
    puVar3 = DAT_0095d4d4;
    iVar7 = 0;
    *DAT_0095d4d4 = (uint)(byte)(&scriptBeginAddress_0x97fb80)[iVar2];
    *(undefined2 *)((int)puVar3 + 10) = 0;
    if ((DAT_0095f6d0 == '\x02') || ((DAT_008e12ac & 0xa00) != 0)) {
      *(undefined2 *)((int)puVar3 + 10) = 1;
    }
    uVar12 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar2));
    uVar8 = (uint)((ulonglong)uVar12 >> 0x20);
    if ((short)uVar12 == 0x4000) {
      *(undefined2 *)(puVar3 + 2) = 2;
      puVar11 = (undefined *)((int)puVar3 + 0x11);
      do {
        *(short *)(puVar11 + -5) = (short)iVar7;
        uVar8 = commandArgParser(uVar8 & 0xffff0000 |
                                 (uint)(ushort)(short)(char)(&DAT_0097fb83)[iVar2]);
        uVar9 = extraout_var_01;
        if (((short)uVar8 == 0) ||
           (sVar6 = commandArgParser(uVar8 & 0xffff0000 |
                                     (uint)(ushort)(short)(char)(&DAT_0097fb83)[iVar2]),
           uVar9 = extraout_var_02, sVar6 == 3)) {
          *puVar11 = 2;
        }
        else {
          uVar5 = commandArgParser(CONCAT22(extraout_var,(short)(char)(&DAT_0097fb83)[iVar2]));
          *puVar11 = uVar5;
          uVar9 = extraout_var_03;
        }
        uVar5 = commandArgParser(CONCAT22(uVar9,(ushort)(byte)(&DAT_0097fb84)[iVar2]));
        puVar11[1] = uVar5;
        iVar7 = iVar7 + 1;
        puVar11 = puVar11 + 8;
        uVar8 = extraout_EDX;
      } while (iVar7 < (int)(uint)*(ushort *)(puVar3 + 2));
    }
    else {
      bVar1 = (&DAT_0097fb82)[iVar2];
      uVar8 = (uint)uVar12 & 0xffff0000;
      *(ushort *)(puVar3 + 2) = (ushort)bVar1;
      if (bVar1 != 0) {
        puVar11 = (undefined *)((int)puVar3 + 0x11);
        do {
          *(short *)(puVar11 + -5) = (short)*(char *)((int)param_3 + iVar7 + 4);
          uVar8 = commandArgParser(uVar8 & 0xffff0000 |
                                   (uint)(ushort)(short)(char)(&DAT_0097fb83)[iVar2]);
          if (((short)uVar8 == 0) ||
             (uVar8 = commandArgParser(CONCAT22(extraout_var_00,(short)(char)(&DAT_0097fb83)[iVar2])
                                      ), (short)uVar8 == 3)) {
            *puVar11 = 2;
          }
          else {
            uVar8 = commandArgParser(CONCAT22(extraout_var_04,(short)(char)(&DAT_0097fb83)[iVar2]));
            *puVar11 = (char)uVar8;
          }
          uVar8 = commandArgParser(uVar8 & 0xffff0000 | (uint)(byte)(&DAT_0097fb84)[iVar2]);
          puVar11[1] = (char)uVar8;
          iVar7 = iVar7 + 1;
          puVar11 = puVar11 + 8;
        } while (iVar7 < (int)(uint)*(ushort *)(puVar3 + 2));
      }
    }
    FUN_0047f1e0(DAT_0095d53c,0);
    *param_1 = *param_1 + 1;
  }
  else if ((*param_1 == 1) && (iVar7 = FUN_0047f640(DAT_0095d530,1), iVar7 != 0)) {
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 2;
  }
  *param_3 = *param_3 + 1;
  return 0;
}
```

## Command 0x84
### Official name: facePostion
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x84_facePosition(int *param_1,undefined4 param_2,int param_3,int *param_4)

{
  short *psVar1;
  byte bVar2;
  byte bVar3;
  int iVar4;
  char cVar5;
  short sVar6;
  short sVar7;
  short sVar8;
  uint uVar9;
  short *psVar10;
  int iVar11;
  char *pcVar12;
  undefined2 *puVar13;
  
  iVar4 = *param_4;
  bVar2 = (&DAT_0097fb82)[iVar4];
  bVar3 = (&DAT_0097fb83)[iVar4];
  uVar9 = bVar2 & 0xf;
  if (*param_1 != 0) {
    return 0;
  }
  if ((bVar3 & 0x30) == 0) {
    if ((bVar2 & 0xf) != 0) {
      pcVar12 = (char *)(param_3 + 4);
      psVar10 = (short *)(param_3 + 6);
      puVar13 = (undefined2 *)(&DAT_0097fb86 + iVar4);
      param_1 = (int *)uVar9;
      do {
        cVar5 = commandArgParser(puVar13[-1]);
        *pcVar12 = cVar5;
        sVar6 = commandArgParser(*puVar13);
        *psVar10 = sVar6;
        sVar7 = commandArgParser(puVar13[1]);
        psVar10[1] = sVar7;
        sVar6 = (&DAT_0095f8e4)[*pcVar12 * 7];
        if (*psVar10 == 0x4000) {
          if (sVar6 < 0) {
            sVar8 = 0x140;
          }
          else {
            sVar8 = *(short *)((int)&DAT_0095f8ec + *pcVar12 * 0xe);
          }
          *psVar10 = sVar8;
        }
        if (sVar7 == 0x4000) {
          if (sVar6 < 0) {
            sVar6 = 0xe0;
          }
          else {
            sVar6 = *(short *)((int)&DAT_0095f8ec + *pcVar12 * 0xe + 2);
          }
          *psVar10 = sVar6;
        }
        *(short *)((int)&DAT_0095f8ec + *pcVar12 * 0xe) = *psVar10;
        cVar5 = *pcVar12;
        psVar1 = psVar10 + 1;
        puVar13 = puVar13 + 3;
        psVar10 = psVar10 + 2;
        pcVar12 = pcVar12 + 1;
        param_1 = (int *)((int)param_1 - 1);
        *(short *)((int)&DAT_0095f8ec + cVar5 * 0xe + 2) = *psVar1;
      } while (param_1 != (int *)0x0);
    }
    iVar11 = 0;
    if ((bVar2 & 0xf) != 0) {
      puVar13 = (undefined2 *)(param_3 + 6);
      do {
        FUN_00435d50((int)*(char *)(param_3 + 4 + iVar11),bVar3 & 3,*puVar13,puVar13[1]);
        iVar11 = iVar11 + 1;
        puVar13 = puVar13 + 2;
      } while (iVar11 < (int)uVar9);
    }
  }
  else if (((bVar3 & 0x30) == 0x10) && ((bVar2 & 0xf) != 0)) {
    pcVar12 = (char *)(param_3 + 4);
    psVar10 = (short *)(&DAT_0097fb86 + iVar4);
    do {
      cVar5 = commandArgParser(psVar10[-1]);
      *pcVar12 = cVar5;
      if (*psVar10 != 0) {
        FUN_0044f060(*psVar10,(int)*(short *)((int)&DAT_0095f8ec + cVar5 * 0xe));
      }
      if (psVar10[1] != 0) {
        FUN_0044f060(psVar10[1],(int)*(short *)((int)&DAT_0095f8ec + *pcVar12 * 0xe + 2));
      }
      pcVar12 = pcVar12 + 1;
      psVar10 = psVar10 + 3;
      uVar9 = uVar9 - 1;
    } while (uVar9 != 0);
  }
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar4];
  return 1;
}
```

## Command 0x85
### Official name: faceAutoPosition
### My guess: (N/A)

### Code
```cpp
void command_0x85_faceAutoPosition(undefined4 param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  short sVar1;
  
  sVar1 = commandArgParser((uint)(&scriptBeginAddress_0x97fb80 + *param_4) & 0xffff0000 |
                           (uint)(ushort)(short)(char)(&DAT_0097fb83)[*param_4]);
  if (-1 < sVar1) {
    FUN_004596d0(param_3);
    return;
  }
  FUN_00459960(param_4);
  return;
}
```
## Command 0x88
### Official name: faceNo
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x88_faceNo(int *param_1,undefined4 param_2,int param_3,int *param_4)
{
  ushort uVar1;
  int iVar2;
  char cVar3;
  uint uVar4;
  ushort *puVar5;
  int iVar6;
  
  iVar2 = *param_4;
  if (*param_1 == 0) {
    if ((((&DAT_0097fb85)[iVar2] & 0x30) == 0x10) && (iVar6 = 0, (&DAT_0097fb82)[iVar2] != '\0')) {
      puVar5 = (ushort *)(&DAT_0097fb88 + iVar2);
      do {
        cVar3 = commandArgParser(puVar5[-1]);
        *(char *)(iVar6 + 4 + param_3) = cVar3;
        uVar1 = *puVar5;
        if (uVar1 != 0) {
          uVar4 = (uint)uVar1;
          if ((ushort)(uVar1 + 0x8000) < 0x1000) {
            if ((uVar4 & 0xfff) < 0x800) {
              (&DAT_0095d860)[uVar4 & 0x7ff] = (&DAT_0095f8e4)[cVar3 * 7];
            }
            else {
              (&DAT_0095d560)[uVar4 & 0x7ff] = (byte)(&DAT_0095f8e4)[cVar3 * 7] & 1;
            }
          }
        }
        iVar6 = iVar6 + 1;
        puVar5 = puVar5 + 2;
      } while (iVar6 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    }
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 1;
  }
  return 0;
}
```

## Command 0x89
### Official name: faceOn
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x89_faceOn(int *param_1,undefined4 param_2,uint param_3,int *param_4)
{
  byte bVar1;
  int iVar2;
  char cVar3;
  undefined uVar4;
  short sVar5;
  undefined2 uVar6;
  uint uVar7;
  int iVar8;
  int iVar9;
  undefined2 *puVar10;
  undefined2 *puVar11;
  short *psVar12;
  char *pcVar13;
  
  iVar8 = param_3;
  iVar2 = *param_4;
  bVar1 = (&DAT_0097fb83)[iVar2];
  if (*param_1 == 0) {
    if ((bVar1 & 0x30) == 0) {
      sVar5 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
      if (sVar5 == 0x4000) {
        param_3 = 2;
        iVar9 = 0;
        puVar10 = (undefined2 *)(iVar8 + 6);
        do {
          *(char *)(iVar9 + 4 + iVar8) = (char)iVar9;
          uVar6 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar2));
          *puVar10 = uVar6;
          iVar9 = iVar9 + 1;
          puVar10 = puVar10 + 1;
          uVar7 = param_3;
        } while (iVar9 < 2);
      }
      else {
        uVar7 = (uint)(byte)(&DAT_0097fb82)[iVar2];
        iVar9 = 0;
        if (uVar7 != 0) {
          puVar10 = (undefined2 *)(param_3 + 6);
          puVar11 = (undefined2 *)(&DAT_0097fb86 + iVar2);
          do {
            uVar4 = commandArgParser(puVar11[-1]);
            *(undefined *)(iVar9 + 4 + param_3) = uVar4;
            uVar6 = commandArgParser(*puVar11);
            *puVar10 = uVar6;
            iVar9 = iVar9 + 1;
            puVar10 = puVar10 + 1;
            puVar11 = puVar11 + 2;
          } while (iVar9 < (int)uVar7);
        }
      }
      param_3 = uVar7;
      if (param_3 != 0) {
        pcVar13 = (char *)(iVar8 + 4);
        puVar10 = (undefined2 *)(iVar8 + 6);
        do {
          (&DAT_0095f8e8)[*pcVar13 * 0xe] = *(undefined *)puVar10;
          FUN_00435d10((int)*pcVar13,bVar1 & 3,*puVar10);
          puVar10 = puVar10 + 1;
          pcVar13 = pcVar13 + 1;
          param_3 = param_3 - 1;
        } while (param_3 != 0);
      }
    }
    else if (((bVar1 & 0x30) == 0x10) && (iVar8 = 0, (&DAT_0097fb82)[iVar2] != '\0')) {
      psVar12 = (short *)(&DAT_0097fb86 + iVar2);
      do {
        cVar3 = commandArgParser(psVar12[-1]);
        *(char *)(iVar8 + 4 + param_3) = cVar3;
        if (*psVar12 != 0) {
          FUN_0044f060(*psVar12,(int)(char)(&DAT_0095f8e8)[cVar3 * 0xe]);
        }
        iVar8 = iVar8 + 1;
        psVar12 = psVar12 + 2;
      } while (iVar8 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    }
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 1;
  }
  return 0;
}
```

## Command 0x8A
### Official name: facePri
### My guess: (N/A)

### Code
```cpp
undefined4 command_0x8a_facePri(int *param_1,undefined4 param_2,uint param_3,int *param_4)

{
  byte bVar1;
  int iVar2;
  char cVar3;
  undefined uVar4;
  short sVar5;
  undefined2 uVar6;
  uint uVar7;
  int iVar8;
  int iVar9;
  undefined2 *puVar10;
  undefined2 *puVar11;
  short *psVar12;
  char *pcVar13;
  
  iVar8 = param_3;
  iVar2 = *param_4;
  bVar1 = (&DAT_0097fb83)[iVar2];
  if (*param_1 == 0) {
    if ((bVar1 & 0x30) == 0) {
      sVar5 = commandArgParser(*(undefined2 *)(&DAT_0097fb84 + iVar2));
      if (sVar5 == 0x4000) {
        param_3 = 2;
        iVar9 = 0;
        puVar10 = (undefined2 *)(iVar8 + 6);
        do {
          *(char *)(iVar9 + 4 + iVar8) = (char)iVar9;
          uVar6 = commandArgParser(*(undefined2 *)(&DAT_0097fb86 + iVar2));
          *puVar10 = uVar6;
          iVar9 = iVar9 + 1;
          puVar10 = puVar10 + 1;
          uVar7 = param_3;
        } while (iVar9 < 2);
      }
      else {
        uVar7 = (uint)(byte)(&DAT_0097fb82)[iVar2];
        iVar9 = 0;
        if (uVar7 != 0) {
          puVar10 = (undefined2 *)(param_3 + 6);
          puVar11 = (undefined2 *)(&DAT_0097fb86 + iVar2);
          do {
            uVar4 = commandArgParser(puVar11[-1]);
            *(undefined *)(iVar9 + 4 + param_3) = uVar4;
            uVar6 = commandArgParser(*puVar11);
            *puVar10 = uVar6;
            iVar9 = iVar9 + 1;
            puVar10 = puVar10 + 1;
            puVar11 = puVar11 + 2;
          } while (iVar9 < (int)uVar7);
        }
      }
      param_3 = uVar7;
      if (param_3 != 0) {
        pcVar13 = (char *)(iVar8 + 4);
        puVar10 = (undefined2 *)(iVar8 + 6);
        do {
          (&DAT_0095f8e9)[*pcVar13 * 0xe] = *(undefined *)puVar10;
          FUN_00435de0((int)*pcVar13,bVar1 & 3,*puVar10);
          puVar10 = puVar10 + 1;
          pcVar13 = pcVar13 + 1;
          param_3 = param_3 - 1;
        } while (param_3 != 0);
      }
    }
    else if (((bVar1 & 0x30) == 0x10) && (iVar8 = 0, (&DAT_0097fb82)[iVar2] != '\0')) {
      psVar12 = (short *)(&DAT_0097fb86 + iVar2);
      do {
        cVar3 = commandArgParser(psVar12[-1]);
        *(char *)(iVar8 + 4 + param_3) = cVar3;
        if (*psVar12 != 0) {
          FUN_0044f060(*psVar12,(int)(char)(&DAT_0095f8e9)[cVar3 * 0xe]);
        }
        iVar8 = iVar8 + 1;
        psVar12 = psVar12 + 2;
      } while (iVar8 < (int)(uint)(byte)(&DAT_0097fb82)[iVar2]);
    }
    *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar2];
    return 1;
  }
  return 0;
}
```

## Command 0xF8
### Official name: mesLogSave
### My guess: (N/A)

### Code
```cpp
undefined4 command_0xF8_mesLogSave(int *param_1,undefined4 param_2,undefined4 param_3,int *param_4)
{
  int iVar1;
  
  iVar1 = *param_4;
  if (*param_1 != 0) {
    return 0;
  }
  FUN_00436030();
  FUN_0044c700();
  *param_4 = *param_4 + (uint)(byte)(&scriptCommandLength_0x0097fb81)[iVar1];
  return 1;
}
```






























