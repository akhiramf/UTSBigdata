# UTSBigdata
1. Cari dan sebutkan 3 DBMS yang bisa digunakan untuk mengelola big data
jawab :
MongoDB, Apache Cassandra, Redis

2. Carilah contoh masalah big data yang bisa dikelola menggunakan salah satu DBMS tersebut, jelaskan mulai dari instalasi sampai CRUD untuk data menggunakan DBMS tersebut. Asumsikan anda akan memecahkan masalah big data yang sudah anda cari contoh tadi, jelaskan kira-kira bagaimana arsitektur dari solusi big data menggunakan DBMS tersebut, gambarkan diagramnya.
jawab :
- instalasi 
1.	Download software mongo
2.	extract file mongodb-win32-i386-2.4.9.zip ke folder XAMPP. rename foldernya menjadi mongodb.  
3.	Buat folder data di  D:\xampp\mongodb\data sebagai lokasi penyimpanan database.
4.	Buka command prompt dan masuklah ke D:\xampp\mongodb\bin dan gunakan perintah ini untuk menjalankan server mongodb.
mongod.exe --dbpath=d:\xampp\mongodb\data
5.	Untuk mengakses mongodb server, buka satu lagi Command Prompt dan masuk ke folder D:\xampp\mongodb\bin
Jalankan perintah :
D:\xampp\mongodb\bin>mongo 127.0.0.1
MongoDB shell version: 2.4.8
connecting to: 127.0.0.1/test
>

-CRUD
1. Tampil Data

//Get All Users
    function getListMahasiswa() {
        $users = $this -> table -> find() -> limit($limit);

        return $users;
    }

2.Tambah Data

  public function createMahasiswa() {
        $nim = $_POST['nim'];
        $nama = $_POST['nama'];

        $insert = array("nim" => $nim, "nama" => $nama);
        $this -> table -> insert($insert);
    }
3.Edit Data

    public function updateMahasiswa($nim) {

        $query = array('nim' => $nim);

        //Get the existing info of the user
        $amahasiswaInfo = $this -> table -> findOne($query);

        //Assign New Values
        $amahasiswaInfo['nim'] = $_POST['nim'];
        $amahasiswaInfo['nama'] = $_POST['nama'];

        //Update the User Info
        $this -> table -> save($amahasiswaInfo);
    }
4. delete  Data

  function deleteMahasiswa($nim) {
        $this -> table -> remove(array('nim' => $nim));
    }
