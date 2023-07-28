# Preamble

Unlike the PC version, the opcode length is not encoded in the opcode themselfs.
Instead, the length is encoded inside the opcode function. The opcode is also responsible to
advance the pointer that points to the current opcode to decode and will also call the function that is
responsible for decoding. After that, the current opcode resides at 0x98B31F, from where the
function pointer to the next command is read. The current opcode point is also to find in that region, at
offset 0x44.

Opcode reside in a table at 0x89b656c, the structs consists of a function pointer to the command function,
a char pointer to the name of the command and and uint32_t that is all 0, probably padding (?)

# RE setup

How to decompile 12Riven for PSP

1. Mount the ISO as a drive in Windows (can be done with the build-in Windows mounting tools)
2. Copy the EBOOT.BIN from ISO:/PSP_GAME/SYSDIR/ to your computer
3. Use [deceboot](https://www.romhacking.net/utilities/1225/) to dercypy the bin file
4. Download [Ghirda](https://github.com/NationalSecurityAgency/ghidra/releases/download/Ghidra_10.3.2_build/ghidra_10.3.2_PUBLIC_20230711.zip)
5. Extract Ghidra and follow the steps to set it up
6. Download the [Allegerx](https://github.com/kotcrab/ghidra-allegrex/releases) for Ghidra
7. Extract the extention and copy the folder into /Ghidra_folder/Ghidra/Processors/
8. Open Ghidra, create a new project and import the decrypted EBOOT.BIN
9. Ghdira should recoconize the processor from the binary and the eboot can de decompiled

How to disassble 12Riven for PSP

1. Download [PPSSPP](https://www.ppsspp.org/download)
2. Load the 12Riven ISO into the emulator and start the game
3. Click on Debug -> Disassembler... to open the disassembler for the running game
4. Click on Debug -> Memory view to get a view of the curretn RAM contents

# Opcodes

Size with a question mark need to be resarched, they seem to be encoded in the command, so they are probably variable in size.

Some opcode point to the same function, but this doesn't mean the size is the same. Inside these functions, there is often a destinction
between the opcodes. These opcodes can also differe in size.

Example Command function:
```c
undefined4 command_0x55_vibEnd_0894aa7c(int param_1)
{
  *(int *)(*(int *)(param_1 + 0x44) + 8) = *(int *)(*(int *)(param_1 + 0x44) + 8) + 2;
  loadNextOpcode_08935360();
  return 0;
}
```
`0x08949298` is a function that seems to be called if a certain opcode is not supported. First opcode that is not supported is 0x57.
Might be a feature that was cut in development.


| Opcode  | Name    | Size    |  Offset   |
|---|---|---|---|
| 0x00  | nop  | 2 |  0x08948288 |
| 0x01   |  end | 2 | 0x089482b4  | 
| 0x02  | if  | ?  | 0x089483b0  |
| 0x03  | int_goto  | ? |  0x0894864c |
| 0x04  | int_call  | ? |  0x08948680 |
| 0x05  | int_return | ? | 0x08948708 |
| 0x06  | ext_goto | 12 | 0x08947cc |
| 0x07  | ext_call | 12 | 0x08948840 |
| 0x08  | ext_return | ? | 0x08948914 |
| 0x09  | reg_calc | 6 (?) | 0x089489d4 |
| 0x0A  | count_clear | 2 | 0x08948dd0 |
| 0x0B  | count_wait | 4 | 0x08948e34 |
| 0x0C  | time_wait  | 4 | 0x08948f7c |
| 0x0D  | pad_wait   | 4 | 0x08949054 |
| 0x0E  | pad_get    | 4 | 0x08949190 |
| 0x0F  | file_read  | 4 | 0x089491e0 |
| 0x10  | file_wait  | 2 | 0x08949244 |
| 0x11  | msg_wind   | 2 | 0x0894c4f0 |
| 0x12  | msg_view   | 2 | 0x0894c53c |
| 0x13  | msg_mode   | 2 | 0x0894c644 |
| 0x14  | msg_pos    | 6 | 0x0894c700 |
| 0x15  | msg_size   | 6 | 0x0894c750 |
| 0x16  | msg_type   | 2 | 0x0894c7a0 |
| 0x17  | msg_cursor | 6 | 0x0894c7ec |
| 0x18  | msg_set    | 4 | 0x0894c83c |
| 0x19  | msg_wait   | 2 | 0x0894c894 |
| 0x1A  | msg_clear  | 2 | 0x0894c914 |
| 0x1B  | msg_line   | 2 | 0x0894c954 |
| 0x1C  | msg_speed  | 2 | 0x0894c9a0 |
| 0x1D  | msg_color  | 2 | 0x0894c9ec |
| 0x1E  | msg_anim   | 2 | 0x0894ca38 |
| 0x1F  | msg_disp   | 0x10 (?) | 0x0894cd7c |
| 0x20  | sel_set    | 4 | 0x0894d5e4 |
| 0x21  | sel_entry  | 6 | 0x0894d638 |
| 0x22  | sel_view   | 2 | 0x894d694  |
| 0x23  | sel_wait   | ? | 0x0894d6e0 |
| 0x24  | sel_style  | 2 | 0x0894d794 |
| 0x25  | sel_disp   | 4(?) | 0x0894d7dc |
| 0x26  | fade_start | 4 | 0x0894a878 |
| 0x27  | fade_wait  | 2 | 0x0894a91c |
| 0x28  | graph_set  | 4 | 0x0894ae94 |
| 0x29  | graph_del  | 2 | 0x0894af04 |
| 0x2A  | graph_copy | 4 | 0x0894b328 |
| 0x2B  | graph_view | 6 | 0x0894af50 |
| 0x2C  | graph_pos  | 6 | 0x0894afb4 |
| 0x2D  | graph_move | var | 0x0894b02c|
| 0x2E  | graph_prio | 4 | 0x0894b148 |
| 0x2F  | graph_anim | 4 | 0x0894b198 |
| 0x30  | graph_pal  | 4 | 0x0894b1e8 |
| 0x31  | graph_lay  | 4 | 0x0894b274 |
| 0x32  | graph_wait | 4 | 0x0894b2c4 |
| 0x33  | graph_disp | var * 0x10 | 0x0894c250 |
| 0x34  | effect_start | 4 | 0x0894a7ac |
| 0x35  | effect_end | 2 | 0x0894a800 |
| 0x36  | effect_wait| 2 | 0x0894a84c |
| 0x37  | bgm_set    | 2 | 0x0894dbdc |
| 0x38  | bgm_del    | 2 | 0x0894dc90 |
| 0x39  | bgm_req    | 2 | 0x0894dcd0 |
| 0x3A  | bgm_wait   | 2 | 0x0894dd1c |
| 0x3B  | bgm_speed  | 4 | 0x0894dd70 |
| 0x3C  | bgm_vol    | 2 | 0x0894ddb8 |
| 0x3D  | se_set     | 2 | 0x0894de1c |
| 0x3E  | se_del     | 2 | 0x0894de84 |
| 0x3F  | se_req     | 4 | 0x0894ded0 |
| 0x40  | se_wait    | 4 | 0x0894df20 |
| 0x41  | se_speed   | 4 | 0x0894e124 |
| 0x42  | se_vol     | 4 | 0x0894e180 |
| 0x43  | voice_set  | 2 | 0x0894e20c |
| 0x44  | vocie_del  | 2 | 0x0894e25c |
| 0x45  | voice_req  | 2 | 0x0894e29c |
| 0x46  | voice_wait | 2 | 0x0894e2e8 |
| 0x47  | voice_speed| 4 | 0x0894e3dc |
| 0x48  | voice_vol  | 2 | 0x0894e424 |
| 0x49  | menu_lock  | 2 | 0x0894ab54 |
| 0x4A  | save_lock  | 2 | 0x0894ac94 |
| 0x4B  | save_check | 4 | 0x0894ace8 |
| 0x4C  | save_disp  | 4 | 0x0894a270 |
| 0x4D  | disk_change| 4 | 0x0894a4b0 |
| 0x4E  | jamp_start | 4 | 0x0894ad48 |
| 0x4F  | jamp_end   | 2 | 0x0894ad90 |
| 0x50  | task_entry | 4 | 0x0894aad4 |
| 0x51  | task_del   | 2(?) | 0x0894ab2c |
| 0x52  | cal_disp   | 4 | 0x0894a0c4 |
| 0x53  | title_disp | 2 | 0x0894a160 |
| 0x54  | vib_start  | 4 | 0x0894aa50 |
| 0x55  | vib_end    | 2 | 0x0894aa7c |
| 0x56  | vib_wait   | 2 | 0x0894aaa8 |
| 0x57  | map_view   | 4(?) | 0x08949298 |
| 0x58  | map_entry  | 4(?) | 0x08949298 |
| 0x59  | map_disp   | 4(?) | 0x08949298 |
| 0x5A  | edit_view  | 4(?) | 0x08949298 |
| 0x5B  | chat_send  | 4(?) | 0x08949298 |
| 0x5C  | chat_msg   | 4(?) | 0x08949298 |
| 0x5D  | chat_entry | 4(?) | 0x08949298 |
| 0x5E  | chat_exit  | 4(?) | 0x08949298 |
| 0x5F  | null       |      | 0x00000000 |
| 0x60  | movie_play | 4 | 0x08949368 |
| 0x61  | graph_pos_auto | 12 | 0x0894b378 |
| 0x62  | graph_pos_save | 2 | 0x0894b450 |
| 0x63  | graph_uv_auto  | 16 | 0x0894b49c |
| 0x64  | graph_uv_save  | 2 | 0x0894b5a4 |
| 0x65  | effect_ex      | 38 | 0x089494e4 |
| 0x66  | fade_ex    | var | 0x0894996c |
| 0x67  | vib_ex     | 6 | 0x08949f3c |
| 0x68  | clock_disp | 6 | 0x08949fd4 |
| 0x69  | graph_disp_ex | var * 0x18 | 0x0894c250 |
| 0x6A  | map_init_ex | 4(?) | 0x08949298 |
| 0x6B  | map_point_ex | 4(?) | 0x08949298 |
| 0x6C  | map_route_ex | 4(?) | 0x08949298 |
| 0x6D  | quickk_save  | 2 | 0x0894adc4 |
| 0x6E  | trace_spc    | 2 | 0x0894d52c |
| 0x6F  | sys_msg      | 4 | 0x0894a318 |
| 0x70  | skip_lock    | 2 | 0x0894abd4 |
| 0x71  | key_lock     | 2 | 0x0894ab94 |
| 0x72  | graph_disp2  | var * 0x10 | 0x0894c250 |
| 0x73  | msg_disp2    | 12 | 0x0894cd7c |
| 0x74  | sel_disp2  | 6 | 0x0894d7dc |
| 0x75  | date_disp  | 8 | 0x0894a040 |
| 0x76  | vr_disp | 4 (?) | 0x08949298 |
| 0x77  | vr_select | 4 (?) | 0x08949298 |
| 0x78   | vr_reg_calc | 4 (?) | 0x08949298 |
| 0x79  | vr_msg_disp | 4 (?) | 0x08949298 |
| 0x7A  | map_select | 4 (?) | 0x08949298 |
| 0x7B  | ecg_set | 4 (?) | 0x08949298 |
| 0x7C | ev_init | 4 (?) | 0x08949298 |
| 0x7D | ev_disp | 4 (?) | 0x08949298 |
| 0x7E  | ev_anim | 4 (?) | 0x08949298 |
| 0x7F | eye_lock | 2 | 0x0894ac14 |
| 0x80 | msg_log | 4 | 0x0894d5b8 |
| 0x81 | graph_scale_auto | 16 | 0x0894b5f0 |
| 0x82 | movie_start | 2 (?) | 0x089492f8 |
| 0x83 | move_end | 2 (?) | 0x08949330 |
| 0x84 | fade_ex_start | 6 | 0x08949bf0 |
| 0x85 | fade_ex_wait | 2 | 0x08949ddc |
| 0x86 | breath_lock | 2 | 0x0894ac54 |
| 0x87 | g3d_disp | 2(?) | 0x0894e46c |
| 0x88 | staff_start | 6 | 0x0894e4a4 |
| 0x89 | staff_end | 2 | 0x0894e4f8 |
| 0x8A | staff_wait | 2 | 0x0894e538 |
| 0x8B | scroll_lock | 2 | 0x0894e564 |





















































