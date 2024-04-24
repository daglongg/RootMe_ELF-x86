# ELF x86 - 0 protection

Download the file and use the tool `Exeinfo PE` to check the file information. I realize this file is not file exe of Windows.  It's file GCC

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/e41da8b5-bae9-4d92-aaa4-ef407840521d)

I will run it on the Kali to see how it works. 

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/e939dbd9-0920-45ed-9776-d31ded90d669)

 I started static analysis to see what it does. This program asks password and checks password với `123456789`.  If you enter it correctly, it will return `Bien joue, vous pouvez valider l'epreuve avec le pass`. If it is wrong, it will return `Dommage, essaye encore une fois.`

 ![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/d57370f9-42e5-4a28-b10a-1a7b11abc09d)

 Show flag is `123456789`

 # ELF x86 - Basique
Download the file and use the tool 'Exeinfo PE' to check the file information file. And this file is not file exe for Windows. This is file GCC

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/43fd24f3-6b7f-46ac-adde-0100e756d6f9)

Show i will run file on the Kali to see how it works. Program required enter the username and if incorrect program display `Bad username`

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/f8ce04dc-bd5f-415d-b43d-b0ea017f2138)

Use IDA32 to static anlysis program this. Enter user `john` and password `the ripper` and we has flag is `987654321`

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/d92f2fe2-edcc-4aa6-b4d4-5a08fa15b6b6)

Flag: `987654321`

# PE x86 - 0 protection

Download the file and use the tool `Exeinfo PE` to check the information file. And file it is exe Windown and this is file 32bit.

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/489d4db6-7142-463f-8582-282a6b3f05a8)

Run file and i see notification `Usage: ch15.exe pass`. 

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/3090ceb3-777d-41ba-9507-4053643880c6)

I think this program check the string when i give. If pass correct  program will display `Gratz man`. And wrong display `Wrong password`. And pass is 

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/2867a931-af3b-43ff-80f6-e634448f3c51)

Flag: `SPaCIoS`

# ELF C++ - 0 protection

Download the file and use the tool 'Exeinfo PE' to check the information file. And this file it is file GCC and run in Linux

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/bd165439-b57c-41fd-bade-f828a58dfa2f)

Run file and i see this file request password

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/67550b63-a0b3-4d76-937b-f9f4a3926d8c)

Use `IDA32` to `statics analysic` program and i see when we enter password, it to calll funtion check and return result. Show i'll approach it differently. I use `db`g to `dynamic analysis`.

Download DBG: `sudo apt-get install libc6-dbg gdb valgrind\n`

Download GEF: `wget -O ~/.gdbinit-gef.py -q https://gef.blah.cat/py`

  `echo source ~/.gdbinit-gef.py >> ~/.gdbinit`

Some commands that I thought I would let you know about. You should see if the main function is really named main or named start. Because some programs the main function will be named start. And set up break point `b * main`.
and i see location `0x8048a9d` has funtion cmp input with password. Set break point theree and jump to this.

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/e097d7bd-a7c3-4b2b-b0fb-424b8e65daa7)

Flag: `Here_you_have_to_understand_a_little_C++_stuffs`

# ELF x64 - Golang basique

Download the file and use the tool 'Exeinfo PE' to check the information file. And this file it is file GCC and run in Linux

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/8681fe76-9949-4afd-9309-4ee3cc7a0f04)

Run file and i sê thí file request password

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/b6e63d1b-8efd-4e00-bd04-28971b40b86a)

User IDA64 to static analysis and i see input will XOR with key is 'rootme'

![image](https://github.com/daglongg/RootMe_ELF-x86/assets/138242812/e5c37748-d5c4-44db-9c90-de1593421623)

And i write script python to decode.

```
array = [0x3B, 0x02, 0x23, 0x1B, 0x1B, 0x0C, 0x1C, 0x08, 0x28, 0x1B, 0x21, 0x04, 0x1C, 0x0B]
key = 'rootme'
def decrypt(array, key):
    decrypted = []
    key_length = len(key)
    for i in range(len(array)):
        decrypted.append(array[i] ^ ord(key[i % key_length]))
    return decrypted

decrypted_array = decrypt(array, key)
print(decrypted_array)

```
And t find the flag is `ImLovingGoLand`








