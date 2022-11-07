# writing-week2-frontend-bootcamp

# React. JS Lanjutan - Proptypes

React memiliki kemampuan pengecekan tipe untuk menjalankan pengecekan terhadap props disebuah komponen, kita dapat menggunakan properti khusus yang bernama propTypes. PropTypes  sendiri merupakan library untuk memvalidasi props ini sangat membantu dalam meminimalkan bugs saat mengembangkan sebuh App, jika props tidak benar type (data) nya maka akan muncul warning, umumnya digunakan dengan komponen React. PropTypes mengirimkan berbagai jenis validator yang dapat digunakan untuk memastikan bahwa data yang diterima valid. PropsTypes dapat digunakan dengan install menggunakan perintah :


        npm install prop-types
        
 Kemudian kita import pada component yang ingin kita beri props
 
        import PropTypes from 'prop-types';
        
Contoh penggunaan PropTypes

        import PropTypes from 'prop-types';

        function Header(props) {
        
        return (
            <div>
            <h2>Name: {props.char}</h2>
            <h2>Age: {props.age}</h2>
            </div>
          )
        }
        
        Header.propTypes = {
        char.PropTypes.string,
        age.PropTypes.number
        }
        
Nilai default Prop dapat didefinisikan dengan menambahkan properti khusus defaultProps. Properti defaultProps akan digunakan untuk memastikan bahwa props.char dan props.age akan memiliki sebuah nilai jika tidak ada nilai yang diberikan oleh komponen induknya. Proses pengecekan tipe propTypes akan dijalankan setelah defaultProps berjalan, sehingga proses pengecekan tipe juga akan berlaku untuk defaultProps   
 
 
# React Router

React Router adalah library paling populer di React, Ini menyediakan URL sinkron di browser dengan data yang akan ditampilkan di halaman web Router ReactJS digunakan untuk mengembangkan Aplikasi Web Halaman Tunggal(single application). React Router digunakan untuk menentukan beberapa rute dalam aplikasi. Saat pengguna mengetik URL tertentu ke browser, dan jika jalur URL ini cocok dengan ‘rute’ apa pun di dalam file router, pengguna akan diarahkan ke rute tersebut. React Router memainkan peran penting untuk menampilkan banyak tampilan dalam satu aplikasi halaman. Tanpa React Router, tidak mungkin menampilkan banyak tampilan di aplikasi React. Sebagian besar situs media sosial seperti Facebook, Instagram menggunakan React Router untuk menampilkan banyak tampilan. installasi react-router

# State Management React Redux

# State Management Redux

# Async Actions with Middleware and Thunk
