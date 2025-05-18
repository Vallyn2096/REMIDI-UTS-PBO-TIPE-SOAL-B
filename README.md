using System;
using System.Collections.Generic;

class Buku
{
    public string Judul;
    public string Penulis;
    public int Tahun;
    public string Status;

    public virtual void TampilkanInfo()
    {
        Console.WriteLine(Judul + " | " + Penulis + " | " + Tahun + " | " + Status);
    }
}

class BukuDigital : Buku
{
    public string URL;

    public override void TampilkanInfo()
    {
        Console.WriteLine(Judul + " | " + Penulis + " | " + Tahun + " | " + URL);
    }
}

class Perpustakaan
{
    public string Nama;
    public string Alamat;

    private List<Buku> koleksi = new List<Buku>();

    public void TambahBuku()
    {
        Console.WriteLine("Judul: ");
        string judul = Console.ReadLine();
        Console.WriteLine("Penulis: ");
        string penulis = Console.ReadLine();
        Console.WriteLine("Tahun Terbit: ");
        int tahun = Convert.ToInt32(Console.ReadLine());

        Buku buku = new Buku();
        buku.Judul = judul;
        buku.Penulis = penulis;
        buku.Tahun = tahun;

        koleksi.Add(buku);
        Console.WriteLine("Buku ditambahkan");
    }

    public void TampilkanSemua()
    {
        Console.WriteLine("\nDaftar Buku:");
        for (int i = 0; i < koleksi.Count; i++)
        {
            Console.WriteLine((i + 1) + ". ");
            koleksi[i].TampilkanInfo();
        }
    }

    public void UbahBuku()
    {
        Console.WriteLine("Nomer buku yang mau kamu ubah: ");
        int index = Convert.ToInt32(Console.ReadLine()) - 1;

        if (index >= 0 && index < koleksi.Count)
        {
            Console.WriteLine("Judul baru: ");
            koleksi[index].Judul = Console.ReadLine();
            Console.WriteLine("Penulis baru: ");
            koleksi[index].Penulis = Console.ReadLine();
            Console.WriteLine("Tahun baru: ");
            koleksi[index].Tahun = Convert.ToInt32(Console.ReadLine());

            Console.WriteLine("Data buku diubah");
        }
        else
        {
            Console.WriteLine("Buku nggak ketemu.");
        }
    }

    public void HapusBuku()
    {
        Console.Write("Nomer buku yang akan dihapus ");
        int index = Convert.ToInt32(Console.ReadLine()) - 1;

        if (index >= 0 && index < koleksi.Count)
        {
            koleksi.RemoveAt(index);
            Console.WriteLine("Buku sudah dihapus. ");
        }
        else
        {
            Console.WriteLine("Buku nggak ketemu. ");
        }
    }
}

class Progam
{
    static void Main()
    {
        Perpustakaan perpus = new Perpustakaan();
        perpus.Nama = "perpustakaan kelas B";
        perpus.Alamat = "Jl. Jawa No. 5";

        while (true)
        {
            Console.WriteLine("\n=== PERPUSTAKAAN ===");
            Console.WriteLine("1. Nambah Buku");
            Console.WriteLine("2. Daftar Semua Buku");
            Console.WriteLine("3. Ganti Buku");
            Console.WriteLine("4. Hapus Buku");
            Console.WriteLine("5. Exit");
            Console.Write("Menu: ");
            string pilihan = Console.ReadLine();

            if (pilihan == "1") perpus.TambahBuku();
            else if (pilihan == "2") perpus.TampilkanSemua();
            else if (pilihan == "3") perpus.UbahBuku();
            else if (pilihan == "4") perpus.HapusBuku();
            else if (pilihan == "5") break;
            else Console.WriteLine("pilhan salah bro.");
        }
    }
}
