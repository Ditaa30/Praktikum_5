# Praktikum5

![Screenshot (12)](https://github.com/user-attachments/assets/4ad4409c-2774-4fa5-a137-7b41ae812bc8)
![Screenshot (13)](https://github.com/user-attachments/assets/0436d185-b5f1-4549-804f-017889180c0c)



# * Class Produk

```
package produk;
public class Produk {
    protected String namaProduk;
    protected double harga;
    protected int jumlahStok;
    
    // konstruktor
    public Produk(String namaProduk, double harga, int jumlahStok) {
        this.namaProduk = namaProduk;
        this.harga = harga;
        this.jumlahStok = jumlahStok;
    }
    
    //getter dan setter namaProduk
     public void setNamaProduk(String namaProduk) {
        this.namaProduk = namaProduk;
    }

    public String getNamaProduk() {
        return namaProduk;
    }
    
    //getter dan setter harga
     public void setHarga(double harga) {
        this.harga = harga;
    }

    public double getHarga() {
        return harga;
    }
    
    //getter dan setter jumlahStok
     public void setJumlahStok(int jumlahStok) {
        this.jumlahStok = jumlahStok;
    }

    public int getJumlahStok() {
        return jumlahStok;
    }
    
    
    
    // Method untuk mencetak informasi
    public void displayInfo() {
        System.out.println("NamaProduk: " + namaProduk);
        System.out.println("Harga: " + harga);
        System.out.println("jumlahStok: " + jumlahStok);
        
    }

    
    
    
}
```
# * subclass Elektronik

```

import produk.Produk;


public class Elektronik extends Produk {
    private int garansi;
    
    // konstruktor
    public Elektronik(String namaProduk, double harga, int jumlahStok, int garansi) {
        super(namaProduk, harga, jumlahStok);
        this.garansi = garansi;
    }
    
    // getter dan setter  garansi
     public void setGaransi(int garansi) {
        this.garansi = garansi;
    }

    public int getGaransi() {
        return garansi;
    }
    
    // override displayInfo
    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("garansi: " + garansi + "tahun");
        
    }
    
    
}
```
# * Subclass Pakaian
```

import produk.Produk;


public class Pakaian extends Produk {
    private int ukuran;
    private String warna;
    
    // konstruktor
    public Pakaian(String namaProduk, double harga, int jumlahStok, int ukuran, String warna) {
        super(namaProduk, harga, jumlahStok);
        this.ukuran = ukuran;
        this.warna = warna;
    }
    
    // getter dan setter ukuran
     public void setUkuran(int ukuran) {
        this.ukuran = ukuran;
    }

    public int getUkuran() {
        return ukuran;
    }
    
    // getter dan setter warna
     public void setWarna(String warna) {
        this.warna = warna;
    }

    public String getWarna() {
        return warna;
    }
    
    // override
    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("Ukuran: " + ukuran);
        System.out.println("warna: " + warna);
    }
    
}
```
# * Subclass Makanan

```

import java.util.Date;
import produk.Produk;


public class Makanan extends Produk {
    private Date tanggalkadaluarsa;
    
    // konstruktor
    public Makanan(String namaProduk, double harga, int jumlahStok, Date tanggalkadaluarsa) {
        super(namaProduk, harga, jumlahStok);
        this.tanggalkadaluarsa = tanggalkadaluarsa;
    }
    
    // getter dan setter tanggalkadaluarsa
    public void setTanggalkadaluarsa(Date tanggalkadaluarsa) {
        this.tanggalkadaluarsa = tanggalkadaluarsa;
    }

    public Date getTanggalkadaluarsa() {
        return tanggalkadaluarsa;
    }
    
    //override
    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("Tanggalkadaluarsa: " + tanggalkadaluarsa);
        
    }
}
```

# * class KeranjangBelanja

```

package produk;

import java.util.ArrayList;
import java.util.List;


public class KeranjangBelanja {
    private List<Produk> produk = new ArrayList<>();
    
    public void tambahProduk(Produk produk, int jumlah) {
        for (int i =0; i<jumlah; i++) {
            this.produk.add(produk);
        }
    }
    
    double hitungTotalBelanja() {
        double total = 0;
        for (Produk p : produk) {
            total += p.harga;
        }
        return total; 
    }
    
    public void displayKeranjang() {
        for (Produk p : produk) {
            p.displayInfo();
            System.out.println();        
        }
        System.out.println("Total Belanja: Rp" + hitungTotalBelanja());
    }
}
```

# * class Main

```

import java.util.Date;
import produk.KeranjangBelanja;


public class Main {

    private static int L;
    public static void main(String[] args) {
        
        // Membuat objek-objek produk
        Elektronik Laptop = new Elektronik("Laptop", 7000000, 10,2);
        Pakaian Celana = new Pakaian("Jeans", 200000, 10, L, "Biru denim");
        Makanan Manis = new Makanan("Permen", 5000, 20, new Date(2024, 12, 30));   
        
        // Membuat objek keranjang belanja
        KeranjangBelanja Keranjang = new KeranjangBelanja();
        
        // Menambahkan produk ke keranjang
        Keranjang.tambahProduk (Laptop, 2);
        Keranjang.tambahProduk(Celana, 2);
        Keranjang.tambahProduk(Manis, 3);
        
        // Menampilkan isi keranjang dan total belanja
        Keranjang.displayKeranjang();
        
    }
    
    
}
```

# Output

![Screenshot (16)](https://github.com/user-attachments/assets/c97bc32d-b200-448c-a786-787740b2db7a)
  ![Screenshot (17)](https://github.com/user-attachments/assets/6af29f56-219d-40fe-8bf9-a7136966cd7e)
   ![Screenshot (18)](https://github.com/user-attachments/assets/7ade06f6-1148-4cbd-afc6-d270f005a3d0)


