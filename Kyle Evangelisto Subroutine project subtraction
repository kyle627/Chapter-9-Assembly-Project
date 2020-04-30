;Kyle Evangelisto
; 4/25/2020
; Dr. Mink
; CSC 240

.ORIG x3000           

LEA R0, startup ; startup statements
PUTS
GETC ; Gets user input 
OUT  ; echo echo echo   
AND R1,R1,#0   ; Clear Register 1
ADD R1,R1,R0   ; Store the first number into R1
LEA R0, NEWLINE     ; new linw
PUTS
PUTS    ;MATCH UI 
LEA R0, prompttwo ; Load second prompt tomatch UI
PUTS
GETC      ; 
OUT       ; echo echo echo
AND R2,R2,#0   ; Clear register 2
ADD R2,R2,R0   ; Store the next number into R2
LEA R0, NEWLINE     ; new line
PUTS
PUTS	;MATCH UI      

AND R3,R3,#0  	;Clear register 3
ADD R3,R3,#15
ADD R3,R3,#15
AND R4,R4,#0	;Clear register 4
ADD R4,R3,#2  	;R4 contains 32(ASCII of space character)
ADD R3,R3,#15
ADD R3,R3,#3  	;R3 contains 48

AND R5,R5,#0   ;Clear register 5
ADD R5,R5,R3   ;R5 contains 48(ASCII of '0')
NOT R3,R3

ADD R3,R3,#1   ;R3 contains -48

; Convert the numeric characters into the actual numbers they represent

ADD R1,R1,R3   ; R1 contains actual number (1st one inputed)
ADD R2,R2,R3   ; R2 contains actual number (2nd one inputed)

LEA R0, answer ; Answer prompt
PUTS

; Calculate the 2s complement of 2nd digit to perform substraction

AND R6, R6, #0 ;Clear Register 6
NOT R2,R2
ADD R2,R2,#1   ; R2=-R2
ADD R6,R1,R2   ;Perform substraction(R6=R1-R2)

; determine if result is pos or neg;

BRn neg        ;If result is negative goto label neg
BR pos         ;if result is positive skip 2's complement of result

; if negative take 2s complement.

neg Not R6,R6     

ADD R6,R6,#1
AND R3,R3,#0
ADD R3,R4,#13 ; R3 contains 45(ASCII of '-')
AND R4,R4,#0  
ADD R0,R3,R4  
OUT       

; Convert resulting number back to a printable character and print it

pos ADD R6,R6,R5   ;R6=R6+48
AND R4,R4,#0   ; R4=0
ADD R0,R6,R4   ;   
OUT       ;

HALT      ; 
;Data
startup .STRINGZ   "Please enter a number between 0 and 9: " ;1st prompt
prompttwo .STRINGZ "Enter a number (0 - 9) to subtract from the first number "   ;Prompt number 2
answer .STRINGZ "Result of subtraction: "
NEWLINE .STRINGZ "\n" ;New line character

.END