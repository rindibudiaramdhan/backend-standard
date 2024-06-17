# Backend Standard

Standar konvensi untuk Backend Engineering di sebuah perusahaan melibatkan penyusunan pedoman yang mencakup berbagai aspek seperti penulisan kode, arsitektur sistem, pengelolaan versi, dokumentasi, dan praktik keamanan. Berikut adalah contoh standar konvensi yang bisa diterapkan di perusahaan:

## 1. Penulisan Kode
### 1.1 Penamaan
- Penamaan didasari pada konvensi dan standar dari masing-masing bahasa.
  - PHP: [https://www.php-fig.org/](https://www.php-fig.org/)
  - Golang: [https://go.dev/doc/effective_go](https://go.dev/doc/effective_go)
  - Python: [https://peps.python.org/pep-0000/](https://peps.python.org/pep-0000/)
  - Javascript: [https://google.github.io/styleguide/jsguide.html](https://google.github.io/styleguide/jsguide.html)

Apabila terdapat standar yang tidak tercantum pada konvensi dan standar masing-masing bahasa, maka berikut standar yang disepakati:
#### Variabel
- Gunakan `camelCase` untuk variabel dan nama fungsi.
```python
userName = "JohnDoe"
totalPrice = calculateTotal(cartItems)
```
#### Konstanta
- Gunakan `UPPER_CASE` dengan *underscore* untuk pemisah.
```php
MAX_CONNECTIONS = 100;
TIMEOUT_DURATION = 30;
```
#### Class dan Struktur Data
- Gunakan `PascalCase`.
```python
class UserManager:
    def __init__(self, user_name):
        self.user_name = user_name
```

Catatan:
- Standar ini tidak mengesampingkan standar yang sudah disepakati di masing-masing bahasa, jika ada.
### 1.2 Komentar
- Gunakan komentar untuk menjelaskan logika yang kompleks atau tidak jelas.
- Komentar harus dalam bahasa Inggris.
- Gunakan komentar TODO untuk menandai pekerjaan yang masih perlu diselesaikan.
```python
# Function to calculate total price of items in the cart
def calculateTotal(cartItems):
    total = 0
    for item in cartItems:
        # Add each item's price to total
        total += item.price
    return total

# TODO: Optimize this function for large datasets
```
### 1.3 Format Kode
- Gunakan indentasi 4 spasi.
- Hindari baris kode yang terlalu panjang, maksimal 80 karakter.
- Gunakan linter dan formatter untuk memastikan konsistensi,
  - Javascript:[ESLint](https://eslint.org/)
  - Python: [PyLint](https://pypi.org/project/pylint/)
  - PHP: [Laravel Pint](https://laravel.com/docs/11.x/pint)
  - Golang: [GolangCI-Lint](https://golangci-lint.run/)
```python
def get_user_details(user_id):
    user = database.find_user_by_id(user_id)
    if user is not None:
        return {
            "id": user.id,
            "name": user.name,
            "email": user.email
        }
    else:
        return None
```
## 2. Arsitektur Sistem
### 2.1 Desain API
- Gunakan standar RESTful atau GraphQL sesuai kebutuhan.
  - RESTful: [https://restfulapi.net/](https://restfulapi.net/)
  - GraphSQL: [https://graphql.org/learn/best-practices/](https://graphql.org/learn/best-practices/)
- Endpoint harus konsisten dan mudah dimengerti, gunakan kata kerja HTTP yang sesuai (GET, POST, PUT, DELETE).
```json
GET /api/users/123
{
    "id": 123,
    "name": "John Doe",
    "email": "john.doe@example.com"
}
```

- Berikan respons yang jelas dan informatif, termasuk kode status HTTP yang tepat.
```bash
200 OK
404 Not Found
```

### 2.2 Layered Architecture
- Pisahkan logika bisnis, logika presentasi, dan akses data ke dalam layer yang berbeda.
- Gunakan pola desain yang sesuai (contoh: MVC, MVP, MVVM) untuk memisahkan concerns.
## 3. Pengelolaan Versi
### 3.1 Penggunaan Git
- Gunakan branching model seperti GitFlow atau trunk-based development.
- Nama branch harus deskriptif, gunakan format feature/, bugfix/, release/, hotfix/.
### 3.2 Commit Message
- Gunakan format yang konsisten, contohnya:
```
[Type] Short description
[Body]
[Footer]
```
- Type bisa berupa feat (feature), fix (bug fix), docs (documentation), style (formatting, missing semi colons, etc), refactor, test, chore (maintain).
## 4. Dokumentasi
### 4.1 Kode
- Semua kode harus memiliki dokumentasi yang memadai, baik inline maupun di atas fungsi/kode yang relevan.
- Gunakan tool seperti JSDoc untuk JavaScript, Sphinx untuk Python.
### 4.2 API
- Gunakan tool seperti Swagger/OpenAPI untuk mendokumentasikan API.
- Dokumen API harus mencakup semua endpoint, parameter, respons, dan contoh penggunaan.
## 5. Praktik Keamanan
### 5.1 Pengelolaan Data Sensitif
- Jangan pernah menyimpan data sensitif dalam kode sumber.
- Gunakan variabel lingkungan (environment variables) untuk informasi sensitif seperti kunci API, password, dsb.
### 5.2 Validasi Input
- Validasi semua input dari pengguna untuk mencegah serangan injeksi.
- Gunakan library yang aman untuk menangani input dan output.
### 5.3 Pembaruan dan Pemantauan
- Selalu gunakan versi terbaru dari dependencies.
- Aktifkan logging dan monitoring untuk mendeteksi dan merespons ancaman secara cepat.
## 6. Pengujian
### 6.1 Unit Testing
- Setiap fungsi/kode harus memiliki unit test yang memadai.
- Gunakan framework pengujian yang sesuai (contoh: Jest untuk JavaScript, PyTest untuk Python).
### 6.2 Integration Testing
- Lakukan pengujian integrasi untuk memastikan komponen bekerja bersama dengan baik.
- Mocking dan stubbing harus digunakan untuk mengisolasi bagian yang diuji.
### 6.3 Continuous Integration
- Gunakan CI/CD pipeline untuk memastikan setiap perubahan diuji sebelum digabungkan ke branch utama.
- Integrasikan dengan tools seperti Jenkins, CircleCI, atau GitHub Actions.
## 7. Deployment
### 7.1 Otomatisasi
- Gunakan alat otomatisasi deployment seperti Ansible, Docker, Kubernetes.
- Pastikan bahwa proses deployment terotomatisasi dan dapat direproduksi.
### 7.2 Rollback
- Siapkan mekanisme rollback untuk mengatasi kegagalan deployment.
- Simpan snapshot dari versi sebelumnya untuk memudahkan rollback.
## 8. Review dan Pembaruan Konvensi
Standar konvensi ini harus ditinjau secara berkala.
Buat forum atau sesi khusus untuk mendiskusikan dan memperbarui standar sesuai kebutuhan.
Dengan menerapkan standar konvensi ini, perusahaan dapat memastikan bahwa pengembangan backend berjalan dengan efisien, konsisten, dan aman.
