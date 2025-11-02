<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Kayıt ve Giriş</title>
<style>
body { font-family: Arial; padding: 20px; background: #f5f5f5; }
form { background: #fff; padding: 20px; border-radius: 8px; margin-bottom: 20px; }
input { display: block; margin: 10px 0; padding: 8px; width: 100%; }
button { padding: 10px; background: #007bff; color: #fff; border: none; border-radius: 6px; cursor: pointer; }
button:hover { background: #0056b3; }
</style>
</head>
<body>

<h1>Kayıt Ol</h1>
<form id="registerForm">
    <input type="text" id="regUsername" placeholder="Kullanıcı Adı" required>
    <input type="password" id="regPassword" placeholder="Şifre" required>
    <button type="submit">Kayıt Ol</button>
</form>

<h1>Giriş Yap</h1>
<form id="loginForm">
    <input type="text" id="loginUsername" placeholder="Kullanıcı Adı" required>
    <input type="password" id="loginPassword" placeholder="Şifre" required>
    <button type="submit">Giriş Yap</button>
</form>

<script>
// Kayıt formu
document.getElementById('registerForm').addEventListener('submit', function(e){
    e.preventDefault();
    const username = document.getElementById('regUsername').value;
    const password = document.getElementById('regPassword').value;
    localStorage.setItem('user_' + username, password);
    alert('Kayıt başarılı!');
    document.getElementById('registerForm').reset();
});

// Giriş formu
document.getElementById('loginForm').addEventListener('submit', function(e){
    e.preventDefault();
    const username = document.getElementById('loginUsername').value;
    const password = document.getElementById('loginPassword').value;
    const savedPassword = localStorage.getItem('user_' + username);

    if(savedPassword === password){
        alert('Giriş başarılı! Hoşgeldin, ' + username);
    } else {
        alert('Kullanıcı adı veya şifre hatalı.');
    }
    document.getElementById('loginForm').reset();
});
</script>

</body>
</html>
