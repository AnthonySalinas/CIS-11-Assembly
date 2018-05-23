ExitProcess proto 
WriteInt64 proto 
ReadInt64 proto 
Crlf proto 

.data 
myArray QWORD 10,20,30,40 
.code 
main proc 
	MOV rsi, 0 
	MOV rcx, LENGTHOF myArray 
		BLOOP: 
			mov rax, myArray[rsi * 8] 
			call WriteInt64 
			inc rsi 
		LOOP BLOOP 

call Crlf

MOV rcx, LENGTHOF myArray - 1
SUPERMANLOOP:
	MOV r9, myArray [rcx * 8]
	MOV r13, rcx
	dec r13
	mov r10, myArray[r13 * 8]
	MOV myArray[rcx * 8], r10
	MOV myArray[r13 * 8], r9
LOOP SUPERMANLOOP
 MOV r8, 3
 MOV rsi, 0 
		FLOOP:
			mov rax, myArray[rsi * 8]
			call WriteInt64
			cmp rsi, r8
			jge ENDLOOP
			inc rsi
		LOOP FLOOP
		ENDLOOP:
call ReadInt64
call ExitProcess 
main endp 
end
