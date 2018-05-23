ExitProcess proto
ReadInt64 proto
Crlf proto
WriteInt64 proto
.data
myArray QWORD 5,1,4,2,8
.code
main proc
	MOV rcx, LENGTHOF myArray
	MOV rsi, 0
	ALOOP:
		MOV rax, myArray[rsi * 8]
		call WriteInt64
		inc rsi
	LOOP ALOOP

	
	call Crlf
	MOV rcx, LENGTHOF myArray
	OUTERLOOP:
		push rcx
		MOV rcx, LENGTHOF myArray - 1
		MOV rsi, 0	
		INNERLOOP:
			MOV r9, myArray[rsi * 8]
			mov r11, rsi
			inc r11
			mov r10, myArray[r11*8]
			cmp r9, r10
			jle ENDLOOP
			SWAP: 
				mov myArray[rsi * 8], r10
				mov myArray[r11 * 8], r9
			ENDLOOP:
		
			inc rsi
		LOOP INNERLOOP
		pop rcx
	LOOP OUTERLOOP

	MOV rcx, LENGTHOF myArray
	MOV rsi, 0
	BLOOP:
		MOV rax, myArray[rsi * 8]
		call WriteInt64
		inc rsi
	LOOP BLOOP

	call ReadInt64



call ExitProcess
main endp
end
