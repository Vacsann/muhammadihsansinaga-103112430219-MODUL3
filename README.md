# muhammadihsansinaga-103112430219-MODUL3

# M.AFRIZA-MARANTIKA-103112430271Modul3
# <h1 align="center">Laporan Praktikum Modul 03 <br> Abstract Data Type</h1>
<p align="center">MUHAMMAD IHSAN SINAGA - 103112430219</p>

## Dasar Teori
Abstract Data Type (ADT) atau Tipe Data Abstrak adalah suatu model atau konsep data yang hanya menampilkan apa yang dapat dilakukan oleh data tersebut (operasinya), tanpa menjelaskan bagaimana cara operasinya dilakukan (implementasinya). Dengan kata lain, ADT menekankan pada fungsi dan perilaku data, bukan pada detail penyimpanan atau algoritma yang digunakan.

## Guided

### Menghitung Rata Rata

### mahasiswa.h
```go
#ifndef MAHASISWA_H_INCLUDED
#define MAHASISWA_H_INCLUDED

struct mahasiswa
{
    char nim[10];
    int nilai1, nilai2;
};

void inputMhs(mahasiswa &m);
float rata2(mahasiswa m);

#endif
```

### Mahasiswa.cpp
```go
#include "mahasiswa.h"
#include <iostream>
using namespace std;

void inputMhs(mahasiswa &m)
{
    cout << "input nama = ";
    cin >> (m) .nim;
    cout << "input nilai = ";
    cin >> (m) .nilai1;
    cout << "input niali2 = ";
    cin >> m .nilai2;

}
float rata2(mahasiswa m)
{
    return float(m.nilai1 + m.nilai2) / 2;
}
```

### main.cpp
```go
#include <iostream>
#include "mahasiswa.h"
using namespace std;

int main(){
    mahasiswa mhs;
    inputMhs(mhs);
    cout << "rata rata = " << rata2(mhs);
    return 0;
}
```

## Unguided

### Soal 1

Buat program yang dapat menyimpan data mahasiswa (max. 10) ke dalam sebuah array
dengan field nama, nim, uts, uas, tugas, dan nilai akhir. Nilai akhir diperoleh dari FUNGSI
dengan rumus 0.3*uts+0.4*uas+0.3*tugas.

```go
#include <iostream>
#include <string>
using namespace std;

struct Mahasiswa {
    string nama;
    string nim;
    float uts;
    float uas;
    float tugas;
    float nilaiAkhir;
};

float hitungNilaiAkhir(float uts, float uas, float tugas) {
    return (0.3f * uts) + (0.4f * uas) + (0.3f * tugas);
}

Mahasiswa inputMahasiswa() {
    Mahasiswa mhs;
    cout << "Nama Mahasiswa     : ";
    getline(cin, mhs.nama);
    cout << "NIM Mahasiswa      : ";
    getline(cin, mhs.nim);
    cout << "Nilai UTS          : ";
    cin >> mhs.uts;
    cout << "Nilai UAS          : ";
    cin >> mhs.uas;
    cout << "Nilai Tugas        : ";
    cin >> mhs.tugas;
    cin.ignore();

    mhs.nilaiAkhir = hitungNilaiAkhir(mhs.uts, mhs.uas, mhs.tugas);
    return mhs;
}

void tampilData(const Mahasiswa daftar[], int jumlah) {
    cout << "\n============================================\n";
    cout << "        Data Nilai Mahasiswa         \n";
    cout << "============================================\n";
    for (int i = 0; i < jumlah; i++) {
        cout << "Mahasiswa ke-" << i + 1 << endl;
        cout << "Nama         : " << daftar[i].nama << endl;
        cout << "NIM          : " << daftar[i].nim << endl;
        cout << "UTS          : " << daftar[i].uts << endl;
        cout << "UAS          : " << daftar[i].uas << endl;
        cout << "Tugas        : " << daftar[i].tugas << endl;
        cout << "Nilai Akhir  : " << daftar[i].nilaiAkhir << endl;
        cout << "--------------------------------------------\n";
    }
}

int main() {
    Mahasiswa mahasiswa[10];
    int n;

    cout << "Masukkan jumlah mahasiswa (maks 10): ";
    cin >> n;
    cin.ignore();

    if (n > 10 || n <= 0) {
        cout << "Jumlah tidak valid (1–10)!" << endl;
        return 0;
    }

    for (int i = 0; i < n; i++) {
        cout << "\nInput Data Mahasiswa ke-" << i + 1 << endl;
        mahasiswa[i] = inputMahasiswa();
    }

    tampilData(mahasiswa, n);
    return 0;
}


```

> Output
> ![Screenshot bagian x](ssmodul3unguided1.png)

Program ini digunakan untuk menginput data beberapa mahasiswa, menghitung nilai akhirnya, dan menampilkannya ke layar. Setiap mahasiswa memiliki data berupa nama, NIM, nilai UTS, UAS, dan tugas yang disimpan dalam struktur Mahasiswa. Fungsi hitungNilaiAkhir() menghitung nilai akhir berdasarkan bobot tertentu, inputMahasiswa() digunakan untuk menerima input dari pengguna, dan tampilData() menampilkan seluruh data mahasiswa. Program utama mengatur jumlah mahasiswa, memanggil fungsi input, lalu menampilkan hasil akhirnya.
### Soal 2
Buatlah ADT pelajaran sebagai berikut di dalam file “pelajaran.h”:
Buatlah implementasi ADT pelajaran pada file “pelajaran.cpp”.

Cobalah hasil implementasi ADT pada file “main.cpp”


### pelajaran.h
```go
#ifndef PELAJARAN_H
#define PELAJARAN_H

#include <string>
using namespace std;

struct Pelajaran {
    string namaMapel;
    string kodeMapel;
};

Pelajaran buatPelajaran(string nama, string kode);
void tampilkanPelajaran(Pelajaran pel);

#endif
```
### pelajaran.cpp
```go
#include <iostream>
#include "pelajaran.h"
using namespace std;

Pelajaran buatPelajaran(string nama, string kode) {
    Pelajaran p;
    p.namaMapel = nama;
    p.kodeMapel = kode;
    return p;
}

void tampilkanPelajaran(Pelajaran pel) {
    cout << "Nama Pelajaran : " << pel.namaMapel << endl;
    cout << "Kode Pelajaran : " << pel.kodeMapel << endl;
}

```
### main.cpp
```go
#include <iostream>
#include "pelajaran.h"
using namespace std;

int main() {
    string namaPel = "Struktur Data";
    string kodePel = "STD";

    Pelajaran pel = buatPelajaran(namaPel, kodePel);
    tampilkanPelajaran(pel);

    return 0;
}

```

> Output
> ![Screenshot bagian x](ssmodul3unguided2.png)
Program diatas ini adalah program C++ yang digunakan untuk mengelola data pelajaran dengan cara yang terstruktur. File pelajaran.h berisi struktur Pelajaran yang menyimpan nama dan kode mata pelajaran serta deklarasi fungsi untuk membuat dan menampilkan data pelajaran. File pelajaran.cpp berisi implementasi fungsi-fungsi tersebut, yaitu fungsi buatPelajaran() untuk membuat objek pelajaran baru dan tampilkanPelajaran() untuk menampilkan informasi pelajaran ke layar. File main.cpp berisi fungsi utama yang memanggil kedua fungsi tadi untuk membuat dan menampilkan data pelajaran. Program ini menunjukkan penggunaan struktur data dan pemisahan file header serta implementasi dalam C++.

### Soal 3

Buatlah program dengan ketentuan :
- 2 buah array 2D integer berukuran 3x3 dan 2 buah pointer integer
- fungsi/prosedur yang menampilkan isi sebuah array integer 2D
- fungsi/prosedur yang akan menukarkan isi dari 2 array integer 2D pada posisi tertentu
- fungsi/prosedur yang akan menukarkan isi dari variabel yang ditunjuk oleh 2 buah
pointer

```go
  #include <iostream>
using namespace std;

// Fungsi untuk menampilkan array 3x3
void tampilArray(int (&arr)[3][3]) {
    for (auto &baris : arr) {
        for (auto &nilai : baris)
            cout << nilai << "\t";
        cout << endl;
    }
}

// Template untuk menukar dua nilai apa pun
template <typename T>
void tukar(T &a, T &b) {
    T temp = a;
    a = b;
    b = temp;
}

// Tukar elemen tertentu antara dua array 2D
void tukarElemen(int (&A)[3][3], int (&B)[3][3], int i, int j) {
    tukar(A[i][j], B[i][j]);
}

int main() {
    int A[3][3] = {{1,2,3},{4,5,6},{7,8,9}};
    int B[3][3] = {{10,11,12},{13,14,15},{16,17,18}};

    cout << "Array A sebelum ditukar:\n";
    tampilArray(A);
    cout << "\nArray B sebelum ditukar:\n";
    tampilArray(B);

    tukarElemen(A, B, 1, 1);

    cout << "\nSetelah tukar posisi [1][1]:\nArray A:\n";
    tampilArray(A);
    cout << "\nArray B:\n";
    tampilArray(B);

    int x = 50, y = 100;
    cout << "\nNilai sebelum tukar: x = " << x << ", y = " << y << endl;

    tukar(x, y);

    cout << "Nilai sesudah tukar: x = " << x << ", y = " << y << endl;

    return 0;
}


```

> Output
> ![Screenshot bagian x](ssmodul3unguided3.png)

Program ini adalah program C++ yang menunjukkan penggunaan function overloading dan template untuk menukar nilai. Fungsi tampilArray menampilkan isi array 3x3 ke layar. Fungsi tukar adalah template yang bisa menukar dua nilai apa pun, termasuk integer atau elemen array, dengan menggunakan referensi. Fungsi tukarElemen menukar elemen tertentu antara dua array 3x3 dengan memanggil tukar. Di main(), program membuat dua array A dan B, menampilkan keduanya, menukar elemen [1][1] dari kedua array, lalu menampilkan hasilnya. Program juga menukar dua variabel integer x dan y menggunakan tukar. Program ini mencontohkan manipulasi array, pointer/referensi, dan penggunaan template untuk generalisasi fungsi swap.

## Referensi
