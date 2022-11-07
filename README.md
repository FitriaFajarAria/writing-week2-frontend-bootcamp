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
        
        
# React Router

# State Management React Redux

# State Management Redux

# Async Actions with Middleware and Thunk
