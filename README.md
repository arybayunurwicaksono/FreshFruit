# FreshFruit
Aplikasi keranjang buah sederhana

# Penjelasan Singkat
Aplikasi ini akan menampilkan window dimana pengguna akan memilih buah-buahan untuk dimasukkan kedalam keranjang, beberapa atau sampai penuh. Lalu saat penuh akan muncul notifikasi bahwa keranjang penuh.

# Fungsi BucketEventListener
    Sebagai kendali event saat berhasil atau gagal
    
# Class Diagram
![Diagram](https://user-images.githubusercontent.com/61864279/99414908-db9f9a00-2929-11eb-808a-1d6a31ef2ba6.JPG)

# Logika Pemograman

        Seller Ary;

        public MainWindow()
        {
            InitializeComponent();

            Bucket keranjangBuah = new Bucket(2);
            BucketController bucketController = new BucketController(keranjangBuah, this);

            Ary = new Seller("Ary", bucketController);

            ListBoxBucket.ItemsSource = keranjangBuah.findAll();
        }
        
Awalnya membuat intance seller (Ary) dimana sebagai contoh dari user yang akan menggunakan aplikasi FreshFruit lalu akan memilih buah dan memasukkannya dalam keranjang

        private void Button1_Click(object sender, RoutedEventArgs e)
        {
            Fruit anggur = new Fruit("Anggur");
            Ary.addFruit(anggur);
        }

        private void Button2_Click(object sender, RoutedEventArgs e)
        {
            Fruit Apel = new Fruit("Apel");
            Ary.addFruit(Apel);

        }
        private void Button3_Click(object sender, RoutedEventArgs e)
        {
            Fruit Pisang = new Fruit("Pisang");
            Ary.addFruit(Pisang);

        }
        private void Button4_Click(object sender, RoutedEventArgs e)
        {
            Fruit jeruk = new Fruit("Jeruk");
            Ary.addFruit(jeruk);

        }
Pendeklarasian button untuk memasukkan buah agar masuk kedalam keranjang

        public void onFailed (string msg)
        {
            MessageBox.Show(msg, "Warning");
        }

        public void onSucceed (string msg)
        {
            ListBoxBucket.Items.Refresh();
        }
        
Untuk menampilkan notifikasi sukses/berhasil
        public void addFruit(Fruit fruit)
        {
            if (bucketIsOverload())
            {
                eventListener.onFailed("Ops, keranjang penuh");
            }
            else
            {
                this.bucket.insert(fruit);
                eventListener.onSucceed("Yey, berhasil ditambahkan");
            }
        }
        
        public bool isBucketOverload ()
        {
            return bucket.countItems() >= bucket.getCapacity();
        }
        
Untuk penambahan item dan Pengecekan kapasitas keranjang

        public void removeFruit(Fruit fruit)
        {
            for (int itemPosition = 0; itemPosition < bucket.countItems(); itemPosition++)
            {
                if (bucket.findAll().ElementAt(itemPosition).getName() == fruit.name)
                {
                    bucket.remove(itemPosition);
                    eventListener.onSucceed("Yey, berhasil dihapus");
                }
            }
        }
        
Untuk Penghapusan Item

        public void removeFruit(Fruit fruit)
        {
            for (int itemPosition = 0; itemPosition < bucket.countItems(); itemPosition++)
            {
                if (bucket.findAll().ElementAt(itemPosition).getName() == fruit.name)
                {
                    bucket.remove(itemPosition);
                    eventListener.onSucceed("Yey, berhasil dihapus");
                }
            }
        }



