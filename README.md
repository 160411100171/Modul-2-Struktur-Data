# Modul-2-Struktur-Data
Stack

Kumpulan data yang terurut sesuai bagaimana data tersebut ditambahkan atau dihapus. 
Proses pada stack terjadi pada satu ujung. Ujung ini disebut 'top'. 
Sisi yang berlawanan dengan ujung ini disebut 'base'. 
Stack dalam pengurutan data menggunakan metode LIFO (Last in, First in).

Stack() : membuat tumpukan (stack) baru yang kosong. tidak perlu paramaters dan mengembalikan stack kosong
push(item) :menambahkan item baru ke bagian atas tumpukan. Membutuhkan item dan tidak mengembalikan (return) apapun
pop() : menghapus item teratas dari tumpukan.  Tidak perlu paramaters dan mengembalikan item. Stack berubah
peek() : mengembalikan item teratas dari tumpukan(stack) tetapi tidak menghapusnya. Tidak perlu parameters. Stack tidak berubah
isEmpty() : untuk melihat apakah tumpukan kosong. Tidak perlu parameters dan mengembalikan value dari boolean
size() : mengembalikan jumlah item pada stack. Tidak perlu parameter dan mengembalikan integer

----------------------------------------------------------------------------------------------------------------------------------
Delimiter Matching (Parantheses) – sering digunakan untuk urutan penyelesaian dalam persamaan matematika.

Beberapa tahapan atau algoritma untuk pengecekan parentheses ini adalah :
1.	Baca setiap karakter yang terdapat pada suatu string matematika
2.	Jika karakter adalah kurung buka, maka masukkan dalam stack
3.	Jika karakter adalah kurung tutup, ada beberapa kondisi yang harus diperiksa, yaitu : 
    o	Jika stack dalam keadaan empty, maka jumlah kurung tutup lebih banyak daripada kurung buku
    o	Jika stack dalam keadaan tidak empty, maka maka pop stack, dan cocokkan karakter hasil pop dengan kurung tutup, 
      jika sejenis, maka matched, jika tidak maka jenis kurung tidak sama
4.	Jika semua karakter telah terbaca, dan stack masih dalam keadaan terisi (tidak empty), 
    maka jumlah kurung buka lebih banyak daripada kurung tutup.
    
-----------------------------------------------------------------------------------------------------------------------------------
Konversi Bilangan - 
Pada dunia ilmu komputer seringkali dibutuhkan proses konversi dari suatu bilangan ke bilangan lain, 
misalkan dari bilangan desimal menjadi bilangan biner atau menjadi bilangan octal.

-----------------------------------------------------------------------------------------------------------------------------------
Evaluasi Expressi  Postfix – 
Untuk aritmatikanya idlakukan setelah terdapat dua buah operand sebelum sebuah operator. 
Misalkan : 87+2*, yang berarti (8+7)*2=30, oleh karena itu berikut algoritma untuk mengevaluasi ekspressi aritmatika postfix :
1.	Baca string mulai dari kiri
2.	Jika character yang dibaca adalah sebuah operand, maka push operand tersebut.
3.	Jika character yang dibaca adalah sebuah operator, maka pop dua buah operand yang terdapat pada stack, 
    operasikan dua buah operand tersebut dengan operator, dan push hasil operasinya
4.	hasil akhir adalah angka terakhir yang terdapat di dalam stack

        def stack():
            st=[]
            return (st)
        def push(st,data):
            st.append(data)
        def pop(st):
            data=st.pop()
            return(data)
        def peek(st):
            return(st[len(st)-1])
        def isEmpty(st):
            return (st==[])
        def size(st):
            return(len(st))

        st=stack
        isEmpyt(st)

        push(st,100)
        push(st,23)
        push(st,34)
        pop(st)
        push(st,56)
        pop(st)
        print(st)

        # Delimiter Matching / Parantheses
        def paranthesesCheck(strMath):
            operandStack=stack()
            lenMath=len(strMath)
            openOperand='({['
            closeOperand=')}]'
            #print(lenMath)
            i=0
            Matched=True;
            while i<(lenMath):
                #print(i,'=',strMath[i])
                if strMath[i] in openOperand:
                    push(operandStack,strMath[i])
                    #print(operandStack)
                elif strMath[i] in closeOperand:
                    if not (isEmpty(operandStack)):
                        top=pop(operandStack)
                        #print("top=",top)
                        #print (operandStack)
                        if openOperand.index(top)==closeOperand.index(strMath[i]):
                            Matched=Matched and True
                        else:
                            Matched=Matched and False
                            print ('Kurung Buka dan Kurang Tutup tidak Cocok')
                    else:
                        Matched=Matched and False
                        print('Jumlah Kurung Tutup lebih banyak')
                i=i+1
                #print(Matched)
            if not(isEmpty(operandStack)):
                Matched=False
                print('Jumlah Kurung Buka Lebih banyak')
            return(Matched)

        a='5 x (4 + 5) / ((3 + 2) x (10 - 8)'
        isMatched=paranthesesCheck(b)
        print(isMatched)
        paranthesesCheck('5 x (4 + 5) / ((3 + 2) x (10 - 8))')
        paranthesesCheck('5 x (4 + 5} / ((3 + 2) x (10 - 8))')

        # Membalikkan kata
        kata = input("Masukkan Kata: ")
        st=stack()
        hasil=''
        for i in range(len(kata)):
            push(st,kata[i])
        for i in range(len(kata)):
            hasil = hasil+pop(st)
        print(hasil)

        # Evaluasi Expressi Postfix
        def evaluatePost(postStr):
            operandStack=stack()
            operator='+-/*'
            for i in postStr:
                if i not in operator:
                    push(operandStack,i)
                else:
                    oprnd2=pop(operandStack)
                    oprnd1=pop(operandStack)
                    if i=='+':
                        result=float(oprnd1)+float(oprnd2)
                    elif i=='-':
                        result=float(oprnd1)-float(oprnd2)
                    elif i=='*':
                        result=float(oprnd1)*float(oprnd2)
                    else:
                        result=float(oprnd1)/float(oprnd2)
                    push(operandStack,result)
            return(pop(operandStack))

        print(evaluatePost('45-6*'))

--------------------------------------------------------------------------------------------------------------------------------
Tugas Praktikum

Buatlah suatu modul dengan nama stack, dengan fungsi-fungsi utama yang terdapat dalam modul adalah: 
- stack( ) : inisialisasi stack kosong 
- push(data) : push suatu data ke dalam stack 
- pop ( ) : penghapusan data yang berada pada top of the stack. Return value berupa data yang dihapus dari stack tersebut 
- peep ( ) : informasi yang terdapat pada top of the stack 
- isEmpty( ) : memeriksa stack apakah dalam keadaan kosong 
- size( ) : informasi jumlah data yang terdapat pada stack 

Buatlah modul dengan nama stackImplementation, yang berisi fungsi-fungsi untuk implementasi-implementasi penggunaan konsep stack, antara lain : 

1. reverseWord (kata) : -
    Gunakan fungsi-fungsi yang terdapat pada modul stack untuk membalik suatu kata. Output dari fungsi reverseWord(kata) ini 
    adalah kata yang sudah disusun secara terbalik, seperti berikut :

        In  [ ] : Stack.reverseWord(‘kita’)
        Out [ ] : ‘atik’

2. decToBin(num) : -
Gunakan fungsi-fungsi yang terdapat pada modul stack untuk mengkonversi suatu bilangan decimal menjadi bilangan biner, seperti contoh berikut :

	In    [ ] : stack.decToBin(12)
	Out [ ] : ‘1100’
 
3. evaluatePost(str): -
    Gunakan fungsi-fungsi yang terdapat pada modul stack untuk mengevaluasi ekspressi matematika postfix, dengan return value 
    berupa hasil operasi matematika, dengan ketentuan sebagai berikut : 
    a. antara operand maupun operator, dipisahkan dengan spasi, 
        misalkan : 8 17 + yang berarti 8 + 17 
    b. Tambahkan pengecekan error, antara lain : 
        i. Jika jumlah operand terlalu banyak 
        ii. Jika jumlah operand terlalu sedikit 
        iii. Jika terdapat operasi pembagian dengan nol, seperti 9 0 /, yang berarti 9:0 
    Berikut adalah contoh penggunaan fungsi evaluatePost(str):

        In  [ ] : a=’6 0 81’
                  evaluatePost(a)
        Out [ ] : ‘Error : Terlalu banyak Operand’

        In  [ ] : a=’8 7 + 0 /’
                  evaluatePost(a)
        Out [ ] : ‘Error : Pembagian dengan nol’

        In  [ ] : a=’21 2 + * /’
                  evaluatePost(a)
        Out [ ] : ‘Error : Operand terlalu sedikit’

        In  [ ] : a=’10 11 1 + - 5 *’
                  evaluatePost(a)
        Out [ ] : -10.0


4. parenthesesCheck(str): -
    Gunakan fungsi-fungsi yang terdapat pada modul stack untuk pengecekan kurung pada ekspressi matematika, dengan return value berupa nilai True jika ekspressi matematika sudah benar, dan false jika masih terdapat kesalahan. Selain nilai True dan False, tambahkan pesan error jika terjadi kesalahan, antara lain : 
    o Jumlah kurung buka terlalu banyak 
    o Jumlah kurung tutup terlalu banyak 
    o Kurung buka dan kurung tutup tidaklah cocok 
Contoh penggunaan fungsi dan output yang dihasilkan, dapat dilihat pada contoh berikut:

    In  [ ] : paranthesesCheck(‘{(3+5)*(9-2)}*)
    Out [ ] : (True, ‘Tidak ada Error’)

    In  [ ] : paranthesesCheck(‘{21/(56+2)}*)
    Out [ ] : (False, ‘Jumlah Kurung Buka Lebih banyak’)

    In  [ ] : paranthesesCheck(‘{(4-5)/12+7}*)
    Out [ ] : (False, ‘Jumlah kurung tutup lebih banyak’)

    In   [ ] : paranthesesCheck(‘67*{(5+2)/(12-6)}*)
    Out [ ] : (False, ‘Kurung buka dan Kurung tutup tidak cocok’)

--------------------------------------------------------------------------------------------------------------------------------
Jawaban

## No 1 : ReverseWord / Membalikkan kata
    def stack():
        s=[]
        return(s)

    def push(s,data):
        s.append(data)

    def pop(s):
        data=s.pop()
        return(data)

    def peek(s):
        return(s[len(s)-1])

    def IsEmpty(s):
        return(s==[])

    def size(s):
        return(len(s))

    def ReverseWord(data):
        s=stack()
        for i in range(len(data)):
            push(s,data[i])
        hasil=''
        while not IsEmpty(s):
            hasil+=s.pop()
        return (hasil)
    print(ReverseWord('Fawaizul'))

## No. 2 : Decimal to Biner
    def stack():
        s=[]
        return(s)

    def push(s,data):
        s.append(data)

    def pop(s):
        data=s.pop()
        return(data)

    def peek(s):
        return(s[len(s)-1])

    def IsEmpty(s):
        return(s==[])

    def size(s):
        return(len(s))

    def DectoBiner(angka):
        s = stack()
        while angka > 0:
            biner = int(angka%2)
            push(s,biner)
            angka = (angka-biner) / 2

        hasilBenar = ""

        for i in range(len(s)):
            hasilBenar += (str(pop(s)))
        print("Hasil Biner:",end=" ")
        return (hasilBenar)

    print(DectoBiner(12))

## NO. 3 : evaluatePost
    import Stack

    def evaluatePost(string):
        s=Stack()
        hasil = 0
        for i in string:
            if i == '+':
                if (s.size(s)>2):
                    if (s.peek(s)==' '):
                        s.pop(s)
                    akhir=(Stack.pop(s))
                    if s.peek(s)==' ':
                        s.pop(s)
                    hasil=s.pop(s)+akhir
                    s.push(s,hasil)
                else:
                    return 'Error: operand terlalu sedikit'
            elif i == '-':
                if (s.size(s)>2):
                    if (s.peek(s)==' '):
                        s.pop(s)
                    akhir=(s.pop(s))
                    if s.peek(s)==' ':
                        s.pop(s)
                    hasil=s.pop(s)-akhir
                    s.push(s,hasil)
                else:
                    return 'Error: operand terlalu sedikit'
            elif i == '*':
                if (s.size(s)>2):
                    if (s.peek(s)==' '):
                        s.pop(s)
                    akhir=(s.pop(s))
                    if s.peek(s)==' ':
                        s.pop(s)
                    hasil=akhir*s.pop(s)
                    s.push(s,hasil)
                else:
                    return 'Error: operand terlalu sedikit'
            elif i == '/':
                if (s.size(s)>2):
                    if (s.peek(s)==' '):
                        s.pop(s)
                    akhir=(s.pop(s))
                    if s.peek(s)==0:
                        return 'Error : Pembagian dengan nol'
                    akhir=(s.pop(s))
                    if s.peek(s)==' ':
                        s.pop(s)
                    hasil=s.pop(s)/akhir
                    s.push(s,hasil)
                else:
                    return 'Error: operand terlalu sedikit'
            elif i==' ':
                s.push(s,i)
            else:
                if not(s.isEmpty(s)):
                    if (s.peek(s)!=' '):
                        jumlah=(s.pop(s)*10) + int(i)
                        s.push(s,jumlah)
                    else:
                        s.push(s,int(i))
                else:
                    s.push(s,int(i))
        if s.size(s)>1:
            return 'Error: operand terlalu sedikit'
        else:
            return s.pop(s)

## NO. 4
    def stack():
        operandStack=[]
        return(operandStack)

    def push(operandStack, data):
        operandStack.append(data)

    def pop(operandStack):
        data=operandStack.pop()
        return(data)

    def peek(operandStack):
        return(operandStack[len(operandStack)-1])

    def isEmpty(operandStack):
        return (operandStack == [])

    def size(operandStack):
        return (len(operandStack))

    def paranthesesCheck(strMath):
        operandStack=stack()
        lenMath=len(strMath)
        openOperand='({['
        closeOperand=')}]'
        #print(lenMath)
        i=0
        Matched=True;
        while i<(lenMath):
            #print(i,'=',strMath[i])
            if strMath[i] in openOperand:
                push(operandStack,strMath[i])
                #print(operandStack)
            elif strMath[i] in closeOperand:
                if not (isEmpty(operandStack)):
                    top=pop(operandStack)
                    #print("top=",top)
                    #print (operandStack)
                    if openOperand.index(top)==closeOperand.index(strMath[i]):
                        Matched=Matched and True
                    else:
                        Matched=Matched and False
                        print ('Kurung Buka dan Kurang Tutup tidak Cocok')
                else:
                    Matched=Matched and False
                    print('Jumlah Kurung Tutup lebih banyak')
            i=i+1
            print(Matched)
        if not(isEmpty(operandStack)):
            Matched=False
            print('Jumlah Kurung Buka Lebih banyak')
        return(Matched)

    paranthesesCheck('{(3+5)*(9-2)}')
    print(paranthesesCheck)

    paranthesesCheck('{21*(50+2)}')
    print(paranthesesCheck)
