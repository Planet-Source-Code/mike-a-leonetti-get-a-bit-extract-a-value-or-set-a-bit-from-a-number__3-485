<div align="center">

## Get a bit, extract a value, or set a bit from a number


</div>

### Description

These two macros will get/modify the bit in a number according to a position counted from right to left. For example, let's say we had 1101 1111 (223). We would just use my macro to get the 3rd bit from the right which would be a one. We can also modify it to a 0. Or we want to extract the value of the first four bits, all can be done easily!
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Mike A\. Leonetti](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/mike-a-leonetti.md)
**Level**          |Intermediate
**User Rating**    |4.3 (13 globes from 3 users)
**Compatibility**  |C, C\+\+ \(general\)
**Category**       |[Macros](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/macros__3-28.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/mike-a-leonetti-get-a-bit-extract-a-value-or-set-a-bit-from-a-number__3-485/archive/master.zip)

### API Declarations

```
#include <iostream.h>
```


### Source Code

```
/*Bit Getting/Setting*/
//Macros//
#define EXTRACT_BITS_RL(the_val, bits_start, bits_len) ((the_val >> (bits_start - 1)) & ((1 << bits_len) - 1))
#define MODIFY_BIT_RL(the_val, bit_num, bit_val) (bit_val == 0 ? (the_val & (~(1 << (bit_num - 1)))) : (the_val | (1 << (bit_num - 1))))
//End Macros//
//Globals//
int iVal = 0, iShift = 0, iBitVal = 0, iMenu = 1;
//End Globals//
//Prototyes//
void ShowVal();
void ShowMenu();
//End Prototypes//
int main()
	{
		while(iMenu < 4) //Better way of avoiding GOTOs
			{
				if(iMenu == 1)
					{
						cout << "Input Test Value (0 to 255): ";
						cin >> iVal;
					}
				if(iMenu == 0)
					{
						cout << "Enter Bit Position To Be Modified (1 to 8): ";
						cin >> iShift;
						cout << "Enter New Bit Value (0 or 1): ";
						cin >> iBitVal;
						iVal = MODIFY_BIT_RL(iVal, iShift, iBitVal); //Modify the number's bits
					}
				if(iMenu == 2)
					{
						ShowVal();
					}
				if(iMenu == 3)
					{
						cout << "Enter Start: ";
						cin >> iShift;
						cout << "Enter Length: ";
						cin >> iBitVal;
						cout << "Extracted Value: " << EXTRACT_BITS_RL(iVal, iShift, iBitVal) << "\n";
					}
				ShowMenu();
			}
	return(0);
	}
void ShowVal()
	{
		cout << "Binary Values (Right To Left) for \"" << iVal << "\"\n";
		for(int I = 1; I < 9; I++)
			{
				cout << I << ": " << EXTRACT_BITS_RL(iVal, I, 1) << "\n"; //Show bit position (Right to Left)
			}
	}
void ShowMenu()
	{
		//Display menu
		cout << "\n->Program Menu:\n0: Modify \"" << iVal << "\"\n1: Choose New Number\n2: Show Values for \"" << iVal << "\"\n3: Extract Value\n4: Quit\nChoose: ";
		cin >> iMenu;
		cout << "\n";
	}
```

