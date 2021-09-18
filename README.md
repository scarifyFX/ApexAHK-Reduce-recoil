# ApexAHK-Reduce-recoil
I'm making AHK script with auto detect weapon function. This script work fine but have some issue.
I think I would share this script so that everyone can help to improve this script.
I implement from [Updated [Apex Legends NoRecoil Script] - PART 2](https://www.unknowncheats.me/forum/apex-legends/328576-updated-apex-legends-norecoil-script-2-a.html)  and some GitHub ( GitHub link removed because it break the UC rule )
Anyone please leave a problem that u found so I can fix that problem. But I know the recoil pattern is so wried. I will make it better but now I focused on making the auto detect weapon function work perfectly. 

[Original thread](https://www.unknowncheats.me/forum/apex-legends/468608-ahk-auto-detect-weapon-multiple-resolution-support.html)

Script now support [Tientie (Vengefulcrop)](https://www.unknowncheats.me/forum/apex-legends/467406-method-generating-recoil-patterns-ahk-script-development-testing.html) reciol patterns generating method. ( You can see pattern example in file PatternExample.txt )

## Know issue
* This script is for 1920 x 1080, 1680 x 1050, 2560 x 1080, 2560 x 1440
* Random mouse freeze ( Rarely happen )
* in 2k Spitfire may get recognized for l-star (1 person with this issue)
* Updated patterns still aren't perfect.
* To make auto fire work you must bind your secondary shoot key to 9.
* To disable auto fire delete the weapon pattern.
Code:
`(Weapon name)_Pattern := { Delete all of this }`

## Change log

**V 0.2**
R99 recoil updated
R301 recoil updated
Flatline recoil updated
Added 2560x1440
Added 2560x1080 (ultrawide)

## Hotfix
If you want to use this script without hold right button you need to edit the script like this :
```
~$*LButton::
if (GetKeyState("RButton") || RapidMode) {   <<<< Delete this whole line
	Sleep 5
	Loop {
		If (RapidMode) {
		If A_Index < 3
		Click
		Else
		Random, Rand, 1, 2
		If(Rand = 1)
		Click
		Else
		Send % Subshootkey
		}
		X := StrSplit(Active_Pattern[a_index],",")[1]
		Y := StrSplit(Active_Pattern[a_index],",")[2]
		T := StrSplit(Active_Pattern[a_index],",")[3]
		DllCall("mouse_event", UInt, 0x01, UInt, Round(X * modIfier), UInt, Round(Y * modIfier))
		Sleep T
		} until !GetKeyState("LButton","P") || a_index > Active_Pattern.maxindex()
}   <<<< Delete this whole line
Return
```
