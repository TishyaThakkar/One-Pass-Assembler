# One-Pass Assembler for SIC Machine

##  Introduction
This program is an assembler for a hypothetical Simple Instruction Computer (SIC). It reads assembly language instructions from an input file, processes them, and generates object code as output. The assembler performs tasks such as symbol table creation, location counter management, and object code generation in a single pass.

## Files
- [input.txt](/input.txt) - Contains the assembly language instructions.
- [symtab.txt](/symtab.txt) - Symbol table file where labels and their addresses are stored.
- [output.txt](/output.txt) - Intermediate output file used during processing.
- [obj.txt](/obj.txt) - Final object code file.
- [final.txt](/final.txt) - Detailed output with addresses and mnemonic codes.

## Program Components
### Functions
1. findInSYMTAB
   - Description - Searches for a label in the symbol table and returns its address.
   - Parameters - char findLabel[] - the label to search for.
   - Returns - Address of the label if found, otherwise -1.
2. getMnemonicCode
   - Description: Returns the machine code for a given mnemonic.
   - Parameters: char mnemonic[] - the mnemonic to look up.
   - Returns: Machine code for the mnemonic, or -1 if not found.

  ### Main Function
  The main function performs the following steps:
  1. Initialization:
     - Opens the necessary files: input.txt, output.txt, and symtab.txt.
     - Reads the first line of the input file to check for the START directive and initializes the location counter (LOCCTR).
  2. Processing Each Line:
     - Processes each line of the input file, updating the location counter and populating the symbol table.
     - Generates the object code and writes intermediate results to output.txt.
  3. Finalization:
     - Calculates the program length and outputs it.
     - Re-opens output.txt and reads the intermediate results.
     - Generates the object code and writes it to obj.txt and final.txt.
     - Closes all files and removes output.txt.

## How to Run the Program
1. Prepare the Input File:
   - Create an input.txt file with your assembly language instructions.
2. Compile the Program:
   - Use the following command to compile the program:
     ```
     gcc -o assembler assembler.c
     ```
3. Run the Program:
   - Execute the compiled program:
     ```
     ./assembler
     ```
4. Check the Output Files:
   - symtab.txt - Symbol table with labels and addresses.
   - obj.txt - Object code generated from the input instructions.
   - final.txt - Detailed output with addresses, mnemonic codes, and operands.
  
## Example Input
Here is an example of an input.txt file:
```
** START 2000
** LDA FIVE
** STA ALPHA
** LDCH STRING
** STCH C1
ALPHA RESW 1
FIVE WORD 5
STRING BYTE C'HELLO'
C1 RESB 1
** END **
```

## Output Explanation
- symtab.txt - Contains labels and their addresses.
- obj.txt - Contains the final object code for the program.
- final.txt - Contains a detailed breakdown of the program with addresses and codes.

## Note
- The program assumes the input assembly instructions follow the SIC standard and are well-formed.
- Error handling is minimal; ensure the input is correctly formatted for accurate results.
