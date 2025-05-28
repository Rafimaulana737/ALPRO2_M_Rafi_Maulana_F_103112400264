
---

## Dasar teori
Algoritma Selection Sort Pengurutan secara seleksi adalah mencari nilai ekstrim pada sekumpulan data, kemudian meletakkan pada posisi yang seharusnya. Pada penjelasan berikut ini data akan diurut membesar (ascending), dan data dengan indeks kecil ada di "kiri" dan indeks besar ada di "kanan". 1) Cari nilai terkecil di dalam rentang data tersisa 2) Pindahkan/tukar tempat dengan data yang berada pada posisi paling kiri pada rentang data tersisa tersebut. 3) Ulangi proses ini sampai tersisa hanya satu data saja. Pengurutan secara insertion adalah menyisipkan suatu nilai pada posisi yang seharusnya. Berbeda dengan pengurutan seleksi, yang mana pada pengurutan ini tidak dilakukan pencarian nilai ekstrim terlebih dahulu, cukup memilih suatu nilai tertentu kemudian mencari posisinya secara sequential search. Pada penjelasan berikut ini data akan diurut mengecil (descending), dan data dengan indeks kecil ada di "kiri" dan indeks besar ada di "kanan"


---

### Guided
## SOAL1
``` go
package main

import "fmt"

  

func selectionSortAsc(arr []int, n int) {

    var i, j, idxMin, temp int

    for i = 0; i < n-1; i++ {

        idxMin = i

        for j = i + 1; j < n; j++ {

            if arr[j] < arr[idxMin] {

                idxMin = j

            }

        }

        temp = arr[i]

        arr[i] = arr[idxMin]

        arr[idxMin] = temp

    }

}

func selectionSortDesc(arr []int, n int) {

    var i, j, idxMax, temp int

    for i = 0; i < n-1; i++ {

        idxMax = i

        for j = i + 1; j < n; j++ {

            if arr[j] > arr[idxMax] {

                idxMax = j

            }

        }

        temp = arr[i]

        arr[i] = arr[idxMax]

        arr[idxMax] = temp

    }

}

func main() {

    var n, i int

  

    fmt.Scan(&n)

    arr := make([]int, n)

    for i = 0; i < n; i++ {

        fmt.Scan(&arr[i])

    }

    var ganjil []int

    var genap []int

  

    for i = 0; i < n; i++ {

        if arr[i]%2 == 1 {

            ganjil = append(ganjil, arr[i])

        } else {

            genap = append(genap, arr[i])

        }

    }

    selectionSortAsc(ganjil, len(ganjil))

    selectionSortDesc(genap, len(genap))

  

    for i = 0; i < len(ganjil); i++ {

        fmt.Print(ganjil[i], " ")

    }

    for i = 0; i < len(genap); i++ {

        fmt.Print(genap[i], " ")

    }

    fmt.Println()

}
```

![[modul12&13_pengurutan data/output/guided1.png]]
*penjelasan program*

Program ini dibuat untuk mengurutkan sejumlah bilangan bulat positif dengan aturan khusus, yaitu bilangan ganjil harus diurutkan secara membesar (ascending) dan bilangan genap diurutkan secara mengecil (descending), lalu keduanya digabung dengan bilangan ganjil ditempatkan lebih dulu. Program dimulai dengan membaca jumlah bilangan "n", kemudian membaca "n" buah bilangan dan menyimpannya dalam array. Setelah itu, setiap bilangan diperiksa, jika ganjil, dimasukkan ke dalam array "ganjil", jika genap dimasukkan ke array "genap". Kedua array tersebut lalu diurutkan menggunakan "selection sort", jika ganjil menggunakan versi naik (ascending), dan jika genap versi turun (descending). Lalu seluruh isi aray ganjil dicetak terlebih dahulu, dilanjutkan dengan array genap.

## soal2


``` go
package main

import "fmt"

  

type Siswa struct {

    nilai int

    nim   string

}

  

func insertionSort(data []Siswa, n int) {

    var temp Siswa

    var i, j int

  

    for i = 1; i < n; i++ {

        temp = data[i]

        j = i

        for j > 0 && temp.nilai > data[j-1].nilai {

            data[j] = data[j-1]

            j--

        }

        data[j] = temp

    }

}

  

func main() {

    data := []Siswa{

        {nilai: 75, nim: "2310456001"},

        {nilai: 60, nim: "2310456002"},

        {nilai: 90, nim: "2310456003"},

        {nilai: 80, nim: "2310456004"},

        {nilai: 100, nim: "2310456005"},

        {nilai: 65, nim: "2310456006"},

    }

  

    n := len(data)

    insertionSort(data, n)

  

    for i := 0; i < len(data); i++ {

        fmt.Println(data[i].nilai, data[i].nim)

    }

}
```

![[modul12&13_pengurutan data/output/guided2.png]]
Program bertugas untuk mengurutkan nilai-nilai ujian siswa dari yang tertinggi ke yang terendah. Setiap siswa direpresentasikan dengan sebuah struct siswa yang memiliki dua field yaitu nim dan nilai. Data siswa sudah tersedia langsung di dalam program dalam bentuk array slice dari Siswa. Proses pengurutan dilakukan dengan membandingkan nilai antar siswa.


---
## Unguided
*selection short*
## soal1
``` go
package main

import "fmt"

  

func selectionSort(arr []int, panjang int) {

    var temp, i, j, idxMin int

    for i = 0; i < panjang-1; i++ {

        idxMin = i

        for j = i + 1; j < panjang; j++ {

            if arr[j] < arr[idxMin] {

                idxMin = j

            }

        }

        temp = arr[idxMin]

        arr[idxMin] = arr[i]

        arr[i] = temp

    }

}

  

func main() {

    var n, m int

    fmt.Scan(&n)

  

    for i := 0; i < n; i++ {

        fmt.Scan(&m)

        rumah := make([]int, m)

        for j := 0; j < m; j++ {

            fmt.Scan(&rumah[j])

        }

        selectionSort(rumah, m)

  

        for j := 0; j < m; j++ {

            fmt.Print(rumah[j])

  

            if j < m-1 {

                fmt.Print(" ")

            }

        }

        fmt.Println()

    }

}
```

OUTPUT
![[modul12&13_pengurutan data/output/unguided1.png]]
penjelaasan progaaram

Program akan meminta user untuk memasukkan sebuah bilangan bulat "n" yang menyatakan jumlah daerah tempat tinggal kerabat Hercules. Selanjutnya, untuk setiap daerah, user diminta memasukkan jumlah rumah "m" yang kemudian diikuti dengan "m" buah bilangan bulat sebagai nomor-nomor rumah di daerah tersebut. Semua nomor rumah yang dimasukkan akan disimpan dalam slice "rumah", lalu diproses menggunakan fungsi "selectionSort", yaitu algoritma pengurutan dengan cara mencari nilai terkecil dan menukarnya ke posisi yang seharusnya. Pengurutan dilakukan dari indeks ke-0 hingga ke-(m-1). Setelah selesai, seluruh nomor rumah dalam setiap daerah ditampilkan dalam satu baris secara terurut membesar (ascending).

## SOAL2
``` go
package main

import "fmt"

func selectionSort(arr []int, panjang int) {

    var temp, i, j, idxMin int

  

    for i = 0; i < panjang-1; i++ {

        idxMin = i

        for j = i + 1; j < panjang; j++ {

            if arr[j] < arr[idxMin] {

                idxMin = j

            }

        }

  

        temp = arr[idxMin]

        arr[idxMin] = arr[i]

        arr[i] = temp

    }

}

  

func main() {

    var n, m, angka int

    fmt.Scan(&n)

  

    for i := 0; i < n; i++ {

        fmt.Scan(&m)

        var ganjil, genap []int

  

        for j := 0; j < m; j++ {

            fmt.Scan(&angka)

            if angka % 2 == 1 {

                ganjil = append(ganjil, angka)

            } else {

                genap = append(genap, angka)

            }

        }

  

        selectionSort(ganjil, len(ganjil))

        selectionSort(genap, len(genap))

        for j := 0; j < len(ganjil); j++ {

            fmt.Print(ganjil[j], " ")

        }

        for j := len(genap) - 1; j >= 0; j-- {

            fmt.Print(genap[j])

            if j != 0 {

                fmt.Print(" ")

            }

        }

        fmt.Println()

    }

}
```
output
![[modul12&13_pengurutan data/output/unguided2.png]]
penjelasan program
 Program diawali dengan input jumlah daerah n. Untuk setiap daerah, user akan memasukkan jumlah rumah m, diikuti oleh m buah nomor rumah. Program kemudian memisahkan nomor rumah ke dalam dua array berbeda:
> 
 - ganjil untuk nomor rumah yang ganjil (angka % 2 == 1)

 Masing-masing array diurutkan dengan fungsi selectionSort, di mana ganjil diurutkan secara membesar (ascending), dan `genap` diurutkan membesar lalu dicetak dari belakang agar hasil akhirnya menurun (descending). Output yang dihasilkan berupa satu baris per daerah yang menampilkan nomor rumah ganjil yang telah diurutkan diikuti oleh nomor rumah genap yang juga telah diurutkan terbalik.

## soal3
``` go
package main

import "fmt"

  

func insertionSort(arr []int) {

    for i := 1; i < len(arr); i++ {

        temp := arr[i]

        j := i

        for j > 0 && temp < arr[j-1] {

            arr[j] = arr[j-1]

            j--

        }

        arr[j] = temp

    }

}

  

func hitungMedian(data []int) float64 {

    n := len(data)

    insertionSort(data)

    if n%2 == 1 {

        return float64(data[n/2])

    } else {

        return float64(data[n/2-1]+data[n/2]) / 2.0

    }

}

  

func main() {

    var input int

    var data []int

  

    for {

        fmt.Scan(&input)

        if input == -5313 {

            break

        } else if input == 0 {

            if len(data) > 0 {

                copyData := make([]int, len(data))

                copy(copyData, data)

                fmt.Printf("%.2f\n", hitungMedian(copyData))

            }

        } else if input > 0 {

            data = append(data, input)

        }

    }

}
```
![[Cuplikan layar 2025-05-28 223543.png]]
> Program ini membaca serangkaian bilangan bulat satu per satu dari input. Semua angka positif disimpan dalam array data. Bila ditemukan angka 0, maka program akan menghitung **median** dari elemen-elemen yang telah tersimpan. Fungsi hitungMedian akan menyalin array, mengurutkannya menggunakan insertionSort (dari kecil ke besar), lalu menghitung median. Setiap kali angka 0 dimasukkan, median akan dicetak. Proses terus berlangsung hingga angka -5313 dimasukkan, yang menjadi tanda akhir program. Median selalu dihitung dari seluruh data yang telah dimasukkan **sebelum** angka 0.

## soal1
``` go
package main

  

import "fmt"

  

func main() {

    var data []int

    var x int

  

    for {

        fmt.Scan(&x)

        if x < 0 {

            break

        }

        data = append(data, x)

    }

  

    for i := 1; i < len(data); i++ {

        temp := data[i]

        j := i - 1

        for j >= 0 && data[j] > temp {

            data[j+1] = data[j]

            j--

        }

        data[j+1] = temp

    }

  

    for i := 0; i < len(data); i++ {

        fmt.Printf("%d ", data[i])

    }

    fmt.Println()

  

    if len(data) < 2 {

        fmt.Println("Data berjarak tidak tetap")

        return

    }

  

    jarak := data[1] - data[0]

    sama := true

    for i := 1; i < len(data)-1; i++ {

        if data[i+1]-data[i] != jarak {

            sama = false

            break

        }

    }

  

    if sama {

        fmt.Printf("Data berjarak %d\n", jarak)

    } else {

        fmt.Println("Data berjarak tidak tetap")

    }

}

```
output
![[unguided 1.png]]
penjelasan program
Program ini berfungsi untuk membaca sekumpulan bilangan bulat dari pengguna, kemudian mengurutkan bilangan tersebut, menampilkannya, serta memeriksa apakah bilangan-bilangan tersebut memiliki jarak yang tetap satu sama lain. Pertama, program mendeklarasikan slice data untuk menyimpan input dan variabel x untuk menampung sementara setiap angka yang diinputkan. Melalui perulangan tak hingga, program menerima input angka satu per satu menggunakan fungsi fmt.Scan lalu menghentikan proses input jika angka yang dimasukkan bernilai negatif. Setiap angka positif yang diterima akan disimpan ke dalam slice data. Setelah semua data terkumpul, program mengurutkan angka-angka tersebut secara ascending menggunakan algoritma insertion sort yaitu dengan membandingkan setiap elemen dengan elemen-elemen sebelumnya dan menyisipkannya pada posisi yang tepat. Setelah data diurutkan, program menampilkan semua elemen data dalam satu baris yang dipisahkan oleh spasi. Selanjutnya, program melakukan pemeriksaan apakah data memiliki jarak tetap antar elemennya. Jika jumlah elemen kurang dari dua, program langsung menyimpulkan bahwa data tidak berjarak tetap. Jika ada cukup elemen, program menghitung selisih atau jarak antara elemen pertama dan kedua lalu memeriksa apakah seluruh pasangan elemen berikutnya memiliki selisih yang sama. Bila seluruh jarak konsisten, program akan mencetak bahwa data berjarak tetap dengan nilai jaraknya sedangkan bila ada ketidaksesuaian program akan menampilkan pesan bahwa data berjarak tidak tetap.

## soal2
```go

package main

  

import "fmt"

  

func main() {

    var data []int

    var x int

  

    for {

        fmt.Scan(&x)

        if x < 0 {

            break

        }

        data = append(data, x)

    }

  

    for i := 1; i < len(data); i++ {

        temp := data[i]

        j := i - 1

        for j >= 0 && data[j] > temp {

            data[j+1] = data[j]

            j--

        }

        data[j+1] = temp

    }

  

    for i := 0; i < len(data); i++ {

        fmt.Printf("%d ", data[i])

    }

    fmt.Println()

  

    if len(data) < 2 {

        fmt.Println("Data berjarak tidak tetap")

        return

    }

  

    jarak := data[1] - data[0]

    sama := true

    for i := 1; i < len(data)-1; i++ {

        if data[i+1]-data[i] != jarak {

            sama = false

            break

        }

    }

  

    if sama {

        fmt.Printf("Data berjarak %d\n", jarak)

    } else {

        fmt.Println("Data berjarak tidak tetap")

    }

}

```

![[modul12&13_pengurutan data/output/unguided2.png]]
penjelasan program
Program dimulai dengan membaca jumlah buku yang ada di perpustakaan, kemudian setiap data buku dibaca satu per satu dan disimpan ke dalam array pustaka yang bertipe DaftarBuku. Setiap buku terdiri dari ID, judul, penulis, penerbit, jumlah eksemplar, tahun terbit, dan rating. Setelah seluruh data buku dimasukkan menggunakan prosedur DaftarkanBuku, program mencari buku dengan rating tertinggi dan menampilkannya sebagai buku terfavorit menggunakan prosedur CetakTerfavorit. Langkah selanjutnya, semua buku diurutkan berdasarkan rating menggunakan prosedur UrutBuku, yang mengimplementasikan algoritma insertion sort descending. Setelah proses pengurutan selesai, lima judul buku dengan rating tertinggi ditampilkan melalui prosedur Cetak5Terbaru. Lalu program membaca sebuah rating yang ingin dicari oleh pengguna. Jika ditemukan, informasi lengkap buku tersebut ditampilka, jika tidak maka ditampilkan pesan bahwa tidak ada buku dengan rating tersebut.