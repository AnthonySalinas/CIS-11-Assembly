ExitProcess proto
ReadInt64 proto
WriteInt64 proto
Crlf proto

.data
myArray QWORD 10,20,30,40,50,60
.code
main proc

MOV rsi, 0
MOV rcx, LENGTHOF myArray
	YOLOOP:
		MOV rax, myArray[rsi * 8]
		call WriteInt64
		inc rsi
	LOOP YOLOOP
	MOV rsi, 0
	MOV rcx, LENGTHOF myArray - 1
		SWOOP:
			MOV r9, myArray [rsi * 8] ;holds value 1
			MOV rax, rsi ; holds place one
			inc rsi ; inc to spot two
			MOV r10, myArray[rsi * 8];holds value two
			MOV myArray[rax * 8], r10
			MOV myArray[rsi * 8], r9
			inc rsi
		LOOP SWOOP
		call ReadInt64
	MOV rsi, 0
	MOV rcx, LENGTHOF myArray
	call Crlf
		NOLOOP:
			MOV rax, myArray[rsi * 8]
			call WriteInt64
			inc rsi
		LOOP NOLOOP

	call ReadInt64

main endp
call ExitProcess
end
