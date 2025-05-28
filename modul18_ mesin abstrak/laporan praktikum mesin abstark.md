
---
## dasar teori
Model komputasi terdiri dari data yang dapat diolah dan operasi-operasi dasar pengolahan data tersebut. Mesin abstrak adalah model komputasi yang dirancang di atas model mesin komputasi yang telah ada, yaitu tipe data dan operasi-operasi dasarnya dibuat menggunakan tipe data dan operasi-operasi yang tersedia di mesin di bawahnya. Contoh penerapannya ada pada domino yang kartunya memiliki dua sisi bernilai 0 sampai 6 dan memiliki sistem mengocok, mengambil, dan mengevaluasi kartu, termasuk mencari kartu yang cocok dan memeriksa pasangan kartu.

## unguided
## soal1
``` go
package main

  

import (

    "fmt"

    "math/rand"

    "time"

)

  

type Domino struct {

    suit1 int

    suit2 int

    nilai int

    balak bool

}

  

type Dominoes struct {

    kartu  [28]Domino

    jumlah int

}

  

func buatSetDomino() Dominoes {

    var d Dominoes

    index := 0

    for i := 0; i <= 6; i++ {

        for j := i; j <= 6; j++ {

            nilai := i + j

            balak := i == j

            d.kartu[index] = Domino{i, j, nilai, balak}

            index++

        }

    }

    d.jumlah = 28

    return d

}

  

func kocokKartu(d Dominoes) Dominoes {

    rand.Seed(time.Now().UnixNano())

    for i := 0; i < d.jumlah; i++ {

        j := rand.Intn(d.jumlah)

        d.kartu[i], d.kartu[j] = d.kartu[j], d.kartu[i]

    }

    return d

}

  

func ambilKartu(d Dominoes) (Dominoes, Domino) {

    if d.jumlah == 0 {

        return d, Domino{-1, -1, -1, false}

    }

    d.jumlah--

    return d, d.kartu[d.jumlah]

}

  

func gambarKartu(k Domino, suit int) int {

    if suit == 1 {

        return k.suit1

    }

    return k.suit2

}

  

func nilaiKartu(k Domino) int {

    return k.nilai

}

  

func main() {

    dominoSet := buatSetDomino()

    fmt.Println("Menampilkan 5 kartu awal:")

    for i := 0; i < 5; i++ {

        k := dominoSet.kartu[i]

        fmt.Printf("Kartu: [%d|%d] Nilai: %d Balak: %t\n", k.suit1, k.suit2, k.nilai, k.balak)

    }

  

    dominoSet = kocokKartu(dominoSet)

    fmt.Println("Menampilkan 5 kartu setelah dikocok:")

    for i := 0; i < 5; i++ {

        k := dominoSet.kartu[i]

        fmt.Printf("Kartu: [%d|%d] Nilai: %d Balak: %t\n", k.suit1, k.suit2, k.nilai, k.balak)

    }

  

    fmt.Println("Mengambil 3 kartu:")

    for i := 0; i < 3; i++ {

        var kartu Domino

        dominoSet, kartu = ambilKartu(dominoSet)

        fmt.Printf("Kartu diambil: [%d|%d] Nilai: %d\n", kartu.suit1, kartu.suit2, kartu.nilai)

    }

}
```
## outputt
![[1.png]]
>Program ini adalah implementasi mesin abstrak domino yang mendefinisikan set kartu domino dan operasi fundamental berikutnya, contohnya pembuatan, pengacakkan, dan pengambil kartu. Tipe data Domino menyimpan dua sisi kartu (suit1, suit2), nilai total kartu (nilai), dan status balak (apabila kedua sisi nilainya sama). Dominoes menyimpan array containing 28 kartu yang unik dan jumlah kartu yang masih ada. Program memiliki beberapa fungsi dasar, seperti buatSetDomino untuk melakukan pembuat kartu, kocokKartu untuk mengacak, ambilKartu untuk mengambil kartu dari stock, dan gambarKartu dan nilaiKartu untuk melihat isi dan nilai kartu. Pada fungsi main, program menampilkan 5 kartu awal sebelum dan setelah dikocok, kemungkinan mengambil dan menampilkan 3 kartu dari stock. Implementasi ini sama seperti konsep mesin abstrak.

## soal2
```go
package main

  

import "fmt"

  

type Domino struct {

    Suit1 int

    Suit2 int

}

  

func galiKartu(tumpukan []Domino, target Domino) (Domino, bool) {

    for _, kartu := range tumpukan {

        if kartu.Suit1 == target.Suit1 || kartu.Suit2 == target.Suit1 ||

            kartu.Suit1 == target.Suit2 || kartu.Suit2 == target.Suit2 {

            return kartu, true

        }

    }

    return Domino{}, false

}

  

func sepasangKartu(k1, k2 Domino) bool {

    total := k1.Suit1 + k1.Suit2 + k2.Suit1 + k2.Suit2

    return total == 12

}

  

func main() {

    tumpukan := []Domino{

        {1, 2},

        {3, 4},

        {5, 6},

        {6, 6},

    }

  

    target := Domino{6, 2}

  

    kartuDitemukan, ditemukan := galiKartu(tumpukan, target)

    if ditemukan {

        fmt.Printf("Kartu ditemukan: (%d,%d)\n", kartuDitemukan.Suit1, kartuDitemukan.Suit2)

    } else {

        fmt.Println("Kartu tidak ditemukan.")

    }

  

    k1 := Domino{6, 2}

    k2 := Domino{2, 2}

    if sepasangKartu(k1, k2) {

        fmt.Println("Sepasang kartu, total 12.")

    } else {

        fmt.Println("Bukan sepasang kartu.")

    }

}
```
## output
![[2.png]]
Penjelasan : Program ini membuat kumpulan kartu domino dan mencari kartu di dalamnya yang punya angka sama dengan salah satu sisi kartu target. Kalau ditemukan, kartu itu ditampilkan. Selain itu, kode juga memeriksa apakah dua kartu domino jumlah angka di kedua kartunya sama dengan 12. Jika iya, program bilang itu sepasang kartu. Jadi, program ini untuk mencari kartu yang cocok dan cek apakah dua kartu jumlahnya 12.

## Soal3
```go
package main

  

import (

    "fmt"

    "math/rand"

    "time"

)

  

type Domino struct {

    suit1 int

    suit2 int

    nilai int

    balak bool

}

  

type Dominoes struct {

    kartu  [28]Domino

    jumlah int

}

  

func buatSetDomino() Dominoes {

    var d Dominoes

    indeks := 0

    for i := 0; i <= 6; i++ {

        for j := i; j <= 6; j++ {

            nilai := i + j

            balak := i == j

            d.kartu[indeks] = Domino{i, j, nilai, balak}

            indeks++

        }

    }

    d.jumlah = 28

    return d

}

  

func kocokKartu(d Dominoes) Dominoes {

    rand.Seed(time.Now().UnixNano())

    for i := 0; i < d.jumlah; i++ {

        acak := rand.Intn(d.jumlah)

        d.kartu[i], d.kartu[acak] = d.kartu[acak], d.kartu[i]

    }

    return d

}

  

func ambilKartu(d Dominoes) (Dominoes, Domino) {

    if d.jumlah == 0 {

        return d, Domino{-1, -1, -1, false}

    }

    kartu := d.kartu[d.jumlah-1]

    d.jumlah--

    return d, kartu

}

  

func main() {

    dominoSet := buatSetDomino()

    dominoSet = kocokKartu(dominoSet)

  

    var rangkaian [28]Domino

    var panjang int

  

    var hasilAmbil Dominoes

    var kartu, kartuAwal Domino

  

    hasilAmbil, kartuAwal = ambilKartu(dominoSet)

    dominoSet = hasilAmbil

  

    rangkaian[0] = kartuAwal

    panjang = 1

  

    fmt.Println("Kartu awal:", kartuAwal.suit1, kartuAwal.suit2)

  

    kiri := kartuAwal.suit1

    kanan := kartuAwal.suit2

  

    for dominoSet.jumlah > 0 {

        var hasil Dominoes

        hasil, kartu = ambilKartu(dominoSet)

        dominoSet = hasil

  

        if kartu.suit1 == kiri {

            kiri = kartu.suit2

            for i := panjang; i > 0; i-- {

                rangkaian[i] = rangkaian[i-1]

            }

            rangkaian[0] = kartu

            panjang++

        } else if kartu.suit2 == kiri {

            kiri = kartu.suit1

            for i := panjang; i > 0; i-- {

                rangkaian[i] = rangkaian[i-1]

            }

            rangkaian[0] = kartu

            panjang++

        } else if kartu.suit1 == kanan {

            kanan = kartu.suit2

            rangkaian[panjang] = kartu

            panjang++

        } else if kartu.suit2 == kanan {

            kanan = kartu.suit1

            rangkaian[panjang] = kartu

            panjang++

        }

    }

  

    fmt.Println("Rangkaian akhir kartu:")

    for i := 0; i < panjang; i++ {

        k := rangkaian[i]

        fmt.Printf("[%d|%d] ", k.suit1, k.suit2)

    }

    fmt.Println("\nSelesai, Panjang rangkaian:", panjang)

}

```
## output
![[3.png]]
> Program ini adalah simulasi permainan Gapleh dengan yang memiliki konsep hampir sama dengan domino. kartu domino yang ada dalam struktur Domino yang menyimpan dua sisinya pada kartu (suit1, suit2), nilai total (nilai), dan apakah kartu adalah balak. Struktur Dominoes menyimpan satu set kartu sebanyak kartu 28 unik dan jumlah kartu yang tersisa. Setelah membuat dan mencampur seluruh kartu, program mengambil satu kartu sebagai kartu awal dan melakukan rangkaian permainan. Selanjutnya, program secara otomatis mengambil kartu dan menyusun dari kiri ke kanan dan menghitung panjang rangkaian.

---

## SOAL4
``` go
package main

  

import "fmt"

  

var input string

var pos int

  

func start(text string) {

    input = text

    pos = 0

}

  

func maju() {

    if !eop() {

        pos++

    }

}

  

func eop() bool {

    return pos >= len(input) || input[pos] == '.'

}

  

func cc() byte {

    return input[pos]

}

  

func main() {

    text := "LALEKOLAQALETA.LE."

    start(text)

  

    fmt.Println("Membaca semua karakter:")

    for !eop() {

        fmt.Printf("%c ", cc())

        maju()

    }

    fmt.Println()

  

    start(text)

    jumlahKarakter := 0

    for !eop() {

        jumlahKarakter++

        maju()

    }

    fmt.Println("Jumlah karakter terbaca:", jumlahKarakter)

  

    start(text)

    jumlahA := 0

    for !eop() {

        if cc() == 'A' {

            jumlahA++

        }

        maju()

    }

    fmt.Println("Jumlah huruf A:", jumlahA)

  

    frekuensiA := float64(jumlahA) / float64(jumlahKarakter)

    fmt.Printf("Frekuensi huruf A: %.2f\n", frekuensiA)

  

    start(text)

    jumlahLE := 0

    var prev byte = 0

    for !eop() {

        curr := cc()

        if prev == 'L' && curr == 'E' {

            jumlahLE++

        }

        prev = curr

        maju()

    }

    fmt.Println("Jumlah kata 'LE':", jumlahLE)

}

```
## output
![[4.png]]
>Penjelasan : Program ini membaca teks sampai menemukan titik (.) sebagai tanda akhir. Program menghitung berapa banyak karakter yang terbaca, berapa banyak huruf A yang ada, serta berapa kali huruf "L" diikuti huruf "E" muncul di teks. Setelah itu, program juga menghitung frekuensi huruf A dibandingkan jumlah total karakter. Jadi, intinya kode ini buat baca teks sampai titik dan hitung jumlah karakter, jumlah huruf A, frekuensi huruf A, dan jumlah kemunculan "LE".