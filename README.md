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

React Router adalah library paling populer di React, Ini menyediakan URL sinkron di browser dengan data yang akan ditampilkan di halaman web Router ReactJS digunakan untuk mengembangkan Aplikasi Web Halaman Tunggal(single application). React Router digunakan untuk menentukan beberapa rute dalam aplikasi dan juga digunakan untuk mendefinisikan dan merender komponen berdasarkan jalur yang ditentukan, ini akan menerima komponen dan membuat untuk menentukan apa yang harus dirender.. Saat pengguna mengetik URL tertentu ke browser, dan jika jalur URL ini cocok dengan ‘rute’ apa pun di dalam file router, pengguna akan diarahkan ke rute tersebut. React Router memainkan peran penting untuk menampilkan banyak tampilan dalam satu aplikasi halaman. Tanpa React Router, tidak mungkin menampilkan banyak tampilan di aplikasi React. Sebagian besar situs media sosial seperti Facebook, Instagram menggunakan React Router untuk menampilkan banyak tampilan. installasi react-router


        npm install react-router-dom

Menggunakan React Router


        import React from "react"
        import ReactDOM from "react-dom/client"
        import App from "./App"
        import { BrowserRouter } from "react-router-dom"
        
        const root = ReactDOM.createRoot(document.getElementById("root"))
        root.render(
        
         <React.StrictMode>
         <BrowserRouter>
                <App />
        </BrowserRouter>
        </React.StrictMode>
        
        )
  
biasanya kita akan mengimpor router di halaman index.js dan itu akan membungkus komponen Aplikasi. Router bekerja seperti konteks di React dan menyediakan semua informasi yang diperlukan untuk aplikasi sehingga kita dapat melakukan routing dan menggunakan semua custom hook dari React Router. 

### Defining Routes/Menentukan rute

        
        import { Route, Routes } from "react-router-dom"
        import { Home } from "./Home"
        import { BookList } from "./BookList"

        export function App() {
        return (
             <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/books" element={<BookList />} />
             </Routes>
          )
        }

Setiap kali URL berubah, React Router akan melihat rute yang ditentukan dalam komponen Routes dan itu akan merender konten di elemen prop dari Route yang memiliki jalur yang cocok dengan URL. Dalam contoh di atas jika URL kita adalah "/books" maka komponen BookList akan dirender.

### Handling Navigation


Saat kita mengklik salah satu Link tertentu itu, halaman tersebut akan dimuat yang terkait dengan rute tersebut tanpa memuat ulang halaman web tersebut. Untuk melakukan ini, kita perlu mengimpor komponen <Link>. Komponen ini digunakan untuk membuat tautan yang memungkinkan untuk menavigasi pada URL yang berbeda dan membuat kontennya tanpa memuat ulang halaman web.

        
        import { Route, Routes, Link } from "react-router-dom"
        import { Home } from "./Home"
        import { BookList } from "./BookList"

        export function App() {
        return (
        
        <>
             <nav>
                <ul>
                        <li><Link to="/">Home</Link></li>
                        <li><Link to="/books">Books</Link></li>
                </ul>
             </nav>

             <Routes>
                <Route path="/" element={<Home />} />
                 <Route path="/books" element={<BookList />} />
             </Routes>
       </>
        
           )
        }
 
        
Menambahkan dua tautan ke halaman beranda dan buku, kita juga akan melihat bahwa menggunakan to prop untuk mengatur URL alih-alih href prop yang biasa  digunakan dengan tag anchor. Nav yang  dibuat di bagian atas halaman berada di luar komponen Routes yang berarti ketika kita mengubah halaman, bagian nav ini tidak akan dirender ulang karena hanya konten di komponen Routes akan berubah ketika URL berubah.

### Dynamic Routing
        
        
        <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/books" element={<BookList />} />
                <Route path="/books/:id" element={<Book />} />
        </Routes>
 
Router dinamis yang memiliki parameter :id. Mendefinisikan rute dinamis di React Router. Ketika  memiliki rute dinamis seperti ini, jik ingin mengakses nilai dinamis dalam komponen khusus yang merupakan tempat hook useParams.


        import { useParams } from "react-router-dom"

        export function Book() {
        const { id } = useParams()

         return (
                 <h1>Book {id}</h1>
           )
        }

useParams tidak mengambil parameter dan akan mengembalikan objek dengan key yang cocok dengan parameter dinamis di route. parameter dinamis pada contoh tersebut adalah :id sehingga useParams akan mengembalikan objek yang memiliki kunci id dan nilai kunci itu akan menjadi id aktual di URL. Misalnya, jika URL adalah /books/3, halaman akan merender Buku 3.


        <Route path="*" element={<NotFound />} />
        
"*" akandigunakan seperti menampilkan halaman 404/not found. 

### Nested Routes


        <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/books">
                        <Route index element={<BookList />} />
                        <Route path=":id" element={<Book />} />
                        <Route path="new" element={<NewBook />} />
                </Route>
                <Route path="*" element={<NotFound />} />
        </Routes>        

Nested Router ini cukup sederhana untuk dilakukan yang perlu dilakukan adalah membuat Rute induk (parent) yang memiliki prop jalur yang disetel ke jalur bersama untuk semua komponen Rute anak (child). Kemudian di dalam Rute induk dapat meletakkan semua komponen Rute anak. Satu-satunya perbedaan adalah bahwa prop jalur dari komponen Rute anak tidak lagi menyertakan rute /buku bersama. Juga, rute untuk /books diganti dengan komponen Route yang tidak memiliki prop jalur, tetapi memiliki prop indeks. Semua yang dikatakan adalah bahwa jalur Rute indeks sama dengan Rute induk.

### Outlet Context

Outlet pada dasarnya adalah komponen placeholder yang akan merender apa pun konten halaman kita saat ini. Struktur ini sangat berguna dan membuat berbagi kode antar rute menjadi sangat mudah.


        import { Link, Outlet } from "react-router-dom"

        export function BooksLayout() {
         return (
         
              <>
                 <nav>
                       <ul>
                                <li><Link to="/books/1">Book 1</Link></li>
                                <li><Link to="/books/2">Book 2</Link></li>
                                <li><Link to="/books/new">New Book</Link></li>
                        </ul>
                </nav>

                <Outlet context={{ hello: "world" }} />
             </>
           )
        }

# State Management React Redux

State management library adalah library yang digunakan untuk mengelola state pada suatu aplikasi JavaScript, Redux adalah salah satu library state management yang biasa disandingkan dengan react. Yaitu dengan menyimpan state di satu tempat, sehingga lebih mudah untuk di manage. Biasanya tanpa state management library, kita akan menyimpan state di setiap komponen. Installasi react-redux:


        npm install react-redux

setalah melakukakn installasi selanjutnya kita akan melakukan beberapa tahapan seperti :
1. Buat store (tempat penyimpanan)
2. Buat reducer didalam store
3. Membuat provider
4. Mengambil data dari store dengan menggunakan useSelector

![react-redux](https://miro.medium.com/max/720/0*OAA7rjtyNK1NCaX8.png)

- UI

Ini adalah tampilan aplikasi

- Action

Adalah sebuah function yang mereturn sebuah objek, objek tersebut memiliki sebuah property wajib yaitu type.

Type inilah yang menentukan bagaimana statenya akan diubah.
        
       export default function(state = initialState, action) {
         switch (action.type) {
         case 'ADD_TODO':
         const newState = [...state, action.payload];
        return newState;

        default:
        return state;
          }
        } 
        
- Reducer

Adalah sebuah fungsi yang tugasnya untuk mengolah state yang ada di store. Misal menambah data, menghapus data, mengambil data, dsb. Reducer harus bersifat pure, yang berarti tidak boleh ada sebuah logic yang digunakan di dalamnya

Ada 2 parameter wajib dari reducer, yaitu state dan action.

        function myReducer(previousState, action) => {
        // use the action type and payload to create a new state based on
        // the previous state.
        return newState;
        }
        
- Store

Store adalah tempat untuk menampung state. Store memiliki beberapa fungsi:
1. Izinkan akses ke status melalui getState().
2. Izinkan status diperbarui melalui dispatch(action).
3. Daftar  listeners menggunakan subscribe(listener).
4. Memegang seluruh status aplikasi.

        import { createStore } from 'redux';
        import todoReducer from './reducers';

        const store = createStore(todoReducer);
        
        
### Combining Reducers        

Redux memberi kita fungsi yang disebut combineReducers yang melakukan dua tugas:
1. Menghasilkan fungsi yang memanggil reducer dengan state yang dipilih sesuai dengan key/kuncinya.
2. Menggabungkan hasil menjadi satu objek sekali lagi.


# Async Actions with Middleware and Thunk


1. Middleware merupakan sebuah alat yang digunakan untuk merubah hasil dari request sebelum masuk menjadi response. Middleware Redux dapat melakukan apa saja saat melihat tindakan yang dikirim: mencatat sesuatu, memodifikasi tindakan, menunda tindakan, melakukan panggilan asinkron, dan banyak lagi. Middleware juga memiliki akses ke dispatch dan getState. Itu berarti kita dapat menulis beberapa logika asinkron di middleware, dan masih memiliki kemampuan untuk berinteraksi dengan toko Redux dengan mengirimkan actions. 


        import { client } from '../api/client'

        const delayedActionMiddleware = storeAPI => next => action => {
         if (action.type === 'todos/todoAdded') {
                setTimeout(() => {
         // Delay this action by one second
         next(action)
         }, 1000)
        return
         }

          return next(action)
        }

        const fetchTodosMiddleware = storeAPI => next => action => {
         if (action.type === 'todos/fetchTodos') {
         // Make an API call to fetch todos from the server
        client.get('todos').then(todos => {
          // Dispatch an action with the todos we received
         storeAPI.dispatch({ type: 'todos/todosLoaded', payload: todos })
        })
        }

        return next(action)
        }

2. Thunk adalah konsep pemrograman yang menggunakan fungsi untuk menunda evaluasi/kalkulasi suatu operasi. Redux Thunk adalah middleware yang memungkinkan Anda memanggil pembuat aksi yang mengembalikan fungsi sebagai ganti objek aksi. Fungsi itu menerima metode pengiriman penyimpanan, yang kemudian digunakan untuk mengirim aksi sinkron di dalam isi fungsi setelah operasi asinkron selesai.

        npm install redux-thunk
        
### Contoh Penggunaan redux-thunk


        import { connect } from 'react-redux';
        import { addTodo } from '../actions';
        import NewTodo from '../components/NewTodo';

        const mapDispatchToProps = dispatch => {
         return {
                onAddTodo: todo => {
                dispatch(addTodo(todo));
             }
           };
        };

        export default connect(
        null,
        mapDispatchToProps
        )(NewTodo);
        
Aksi ini akan menggunakan Axios untuk mengirim permintaan POST. Selain menerima metode pengiriman dari status, fungsi yang dikembalikan oleh aksi asinkron bersama Redux Thunk juga menerima metode getState dari penyimpanan.

        
                export const addTodo = ({ title, userId }) => {
                 return (dispatch, getState) => {
                        dispatch(addTodoStarted());

                        console.log('current state:', getState());

                        };
                };
