    M Rafi Maulana f                                 103112400264          

## Dasar teori
Dalam bahasa pemrograman, **alias (type)** digunakan untuk memberikan nama baru pada tipe data yang sudah ada agar lebih ringkas dan sesuai konteks, misalnya `type bilangan int` menjadikan `bilangan` sebagai alias dari `int`. **Struct (structure)** atau record memungkinkan pengelompokan beberapa data yang saling berkaitan ke dalam satu kesatuan yang disebut field, contohnya struct `Mahasiswa` dapat menyimpan `nama`, `umur`, dan `jurusan`. Sementara itu, **array** adalah kumpulan data bertipe sama yang disimpan secara berurutan, memudahkan pengelompokan dan pengolahan data, seperti daftar nilai siswa dalam array `nilai Ketiga konsep ini sangat berguna dalam menyusun program yang rapi, efisien, dan mudah dipahami.


## Soal1
``` go
package main

  

import (

    "fmt"

    "math"

)

  
  

type Titik struct {

    x, y int

}

  

type Lingkaran struct {

    pusat  Titik

    radius int

}

  

func jarak(p, q Titik) float64 {

    dx := float64(p.x - q.x)

    dy := float64(p.y - q.y)

    return math.Sqrt(dx*dx + dy*dy)

}

  
  

func didalam(c Lingkaran, p Titik) bool {

    return jarak(c.pusat, p) <= float64(c.radius)

}

  

func main() {

    var c1, c2 Lingkaran

    var p Titik          

  

    fmt.Scan(&c1.pusat.x, &c1.pusat.y, &c1.radius)

    fmt.Scan(&c2.pusat.x, &c2.pusat.y, &c2.radius)

    fmt.Scan(&p.x, &p.y)

  

    in1 := didalam(c1, p)

    in2 := didalam(c2, p)

  

    if in1 && in2 {

        fmt.Println("Titik di dalam lingkaran 1 dan 2")

    } else if in1 {

        fmt.Println("Titik di dalam lingkaran 1")

    } else if in2 {

        fmt.Println("Titik di dalam lingkaran 2")

    } else {

        fmt.Println("Titik di luar lingkaran 1 dan 2")

    }

}
```
## output

![[Modul7_STRUCT & ARRAY/Output/Soal1.png]]

## Soal2
``` go
package main

  

import (

    "fmt"

    "math"

)
 
const NMAX = 100

func isiArray(arr *[NMAX]int, n *int) {

    fmt.Print("Masukkan jumlah elemen array: ")

    fmt.Scan(n)

    for i := 0; i < *n; i++ {

        fmt.Print("Elemen ke-", i, ": ")

        fmt.Scan(&arr[i])

    }

}
 
func cetakArray(arr [NMAX]int, n int) {

    fmt.Print("Isi array: ")

    for i := 0; i < n; i++ {

        fmt.Print(arr[i], " ")

    }

    fmt.Println()

}
func cetakGanjil(arr [NMAX]int, n int) {

    fmt.Print("Elemen dengan indeks ganjil: ")

    for i := 1; i < n; i += 2 {

        fmt.Print(arr[i], " ")

    }

    fmt.Println()

}

func cetakGenap(arr [NMAX]int, n int) {

    fmt.Print("Elemen dengan indeks genap: ")

    for i := 0; i < n; i += 2 {

        fmt.Print(arr[i], " ")

    }

    fmt.Println()

}
  
func cetakKelipatan(arr [NMAX]int, n int, x int) {

    fmt.Print("Elemen dengan indeks kelipatan ", x, ": ")

    for i := 0; i < n; i++ {

        if i%x == 0 {

            fmt.Print(arr[i], " ")

        }

    }

    fmt.Println()

}
  
func hapusIndeks(arr *[NMAX]int, n *int, index int) {

    if index < 0 || index >= *n {

        fmt.Println("Indeks di luar jangkauan.")

        return

    }

    for i := index; i < *n-1; i++ {

        arr[i] = arr[i+1]

    }

    *n = *n - 1 // Perbaikan dari *n--

    fmt.Println("Array setelah penghapusan:")

    for i := 0; i < *n; i++ {

        fmt.Print(arr[i], " ")

    }

    fmt.Println()

}  

func rataRata(arr [NMAX]int, n int) float64 {

    total := 0

    for i := 0; i < n; i++ {

        total += arr[i]

    }

    return float64(total) / float64(n)

}  

func standarDeviasi(arr [NMAX]int, n int) float64 {

    rerata := rataRata(arr, n)

    total := 0.0

    for i := 0; i < n; i++ {

        selisih := float64(arr[i]) - rerata

        total += selisih * selisih

    }

    return math.Sqrt(total / float64(n))

}

func frekuensi(arr [NMAX]int, n int, target int) int {

    count := 0

    for i := 0; i < n; i++ {

        if arr[i] == target {

            count++

        }

    }

    return count

}

  

func main() {

    var arr [NMAX]int

    var n int

  

    isiArray(&arr, &n)

    cetakArray(arr, n)

    cetakGanjil(arr, n)

    cetakGenap(arr, n)

  

    var x int

    fmt.Print("Masukkan nilai x: ")

    fmt.Scan(&x)

    cetakKelipatan(arr, n, x)

  

    var idxHapus int

    fmt.Print("Masukkan indeks yang ingin dihapus: ")

    fmt.Scan(&idxHapus)

    hapusIndeks(&arr, &n, idxHapus)

  

    fmt.Println("Rata-rata:", rataRata(arr, n))

    fmt.Println("Standar deviasi:", standarDeviasi(arr, n))

  

    var cari int

    fmt.Print("Masukkan bilangan yang ingin dicari frekuensinya: ")

    fmt.Scan(&cari)

    fmt.Println("Frekuensi dari", cari, ":", frekuensi(arr, n, cari))

}
```

## output
![[Modul7_STRUCT & ARRAY/Output/Soal2.png]]
## Soal3

``` go
package main

  

import (

    "fmt"

)

  

func main() {

    var klubA, klubB string

  

    fmt.Print("Klub A : ")

    fmt.Scanln(&klubA)

  

    fmt.Print("Klub B : ")

    fmt.Scanln(&klubB)

  

    var pemenang []string

    pertandingan := 1

  

    for {

        var skorA, skorB int

        fmt.Printf("Pertandingan %d (format: skor %s skor %s): ", pertandingan, klubA, klubB)

        fmt.Scan(&skorA, &skorB)

  

        if skorA < 0 || skorB < 0 {

            break

        }

  

        if skorA > skorB {

            fmt.Printf("Hasil %d: %s menang\n", pertandingan, klubA)

            pemenang = append(pemenang, klubA)

        } else if skorB > skorA {

            fmt.Printf("Hasil %d: %s menang\n", pertandingan, klubB)

            pemenang = append(pemenang, klubB)

        } else {

            fmt.Printf("Hasil %d: Draw\n", pertandingan)

            pemenang = append(pemenang, "Draw")

        }

  

        pertandingan++

    }

  

    fmt.Println("\nPertandingan selesai.")

    fmt.Println("Rekap hasil pertandingan:")

  

    for i, hasil := range pemenang {

        fmt.Printf("Pertandingan %d: %s\n", i+1, hasil)

    }

}
```
## output
![[Modul7_STRUCT & ARRAY/Output/Soal3.png]]
## Soal4
``` go
package main

  

import (

    "fmt"

)

  

const NMAX int = 127

  

type tabel [NMAX]rune

  

func isiArray(t *tabel, n *int) {

    var char rune

    *n = 0

    for {

        fmt.Scanf("%c", &char)

        if char == '.' || *n >= NMAX {

            break

        }

        t[*n] = char

        *n = *n + 1

    }

}

  

func cetakArray(t tabel, n int) {

    for i := 0; i < n; i++ {

        fmt.Printf("%c", t[i])

    }

    fmt.Println()

}

  

func balikanArray(t *tabel, n int) {

    for i := 0; i < n/2; i++ {

        t[i], t[n-1-i] = t[n-1-i], t[i]

    }

}

  

func palindrom(t tabel, n int) bool {

    for i := 0; i < n/2; i++ {

        if t[i] != t[n-1-i] {

            return false

        }

    }

    return true

}

  

func main() {

    var tab tabel

    var m int

  

    fmt.Print("Masukkan karakter (akhiri dengan titik): ")

    isiArray(&tab, &m)

  

    fmt.Print("Reverse teks: ")

    balikanArray(&tab, m)

    cetakArray(tab, m)

  

    // Kembalikan ke bentuk awal

    balikanArray(&tab, m)

  

    fmt.Print("Palindrom: ")

    if palindrom(tab, m) {

        fmt.Println("betul")

    } else {

        fmt.Println("salah")

    }

}
```

## output
![[Soal4.png]]