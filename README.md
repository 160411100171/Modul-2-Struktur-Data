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
