
<html>
<head>
    <meta charset="UTF-8">
    <title>Inicio de Sesión</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; }
        form { max-width: 300px; margin: auto; padding: 20px; border: 1px solid #ccc; border-radius: 5px; }
        input { display: block; width: 100%; padding: 8px; margin: 10px 0; }
        button { width: 100%; padding: 10px; background-color: #4CAF50; color: white; border: none; cursor: pointer; }
        .message { text-align: center; color: red; }
        #lockImage { display: block; margin-top: 20px; text-align: center; font-size: 50px; }
    </style>
</head>
<body>
    <h2>Inicio de Sesión</h2>
    <form id="loginForm">
        <label>Usuario:</label>
        <input type="text" id="username" required>
        <label>Contraseña:</label>
        <input type="password" id="password" required>
        <button type="button" onclick="login()">Iniciar sesión</button>
        <button type="button" onclick="register()">Registrarse</button>
    </form>
    <div class="message" id="message"></div>

    <div id="lockImage">🔒</div>

    <script>
        let usuarios = [{ usuario: "Carlos", contraseña: "2006" }];

        function login() {
            const username = document.getElementById("username").value;
            const password = document.getElementById("password").value;
            const mensaje = document.getElementById("message");
            const lockImage = document.getElementById("lockImage");

            const usuarioEncontrado = usuarios.find(u => u.usuario === username && u.contraseña === password);

            if (usuarioEncontrado) {
                mensaje.innerText = "Inicio de sesión exitoso. Bienvenido, " + username + "!";
                mensaje.style.color = "green";
                lockImage.innerHTML = "🔓";  // Cambia el candado cerrado por el candado abierto
            } else {
                mensaje.innerText = "Usuario o contraseña incorrectos.";
                mensaje.style.color = "red";
            }
        }

        function register() {
            const username = document.getElementById("username").value;
            const password = document.getElementById("password").value;
            const mensaje = document.getElementById("message");

            const usuarioExistente = usuarios.find(u => u.usuario === username);

            if (usuarioExistente) {
                mensaje.innerText = "El usuario ya existe. Pruebe con otro nombre.";
                mensaje.style.color = "red";
            } else {
                usuarios.push({ usuario: username, contraseña: password });
                mensaje.innerText = "Registro exitoso. Ahora puede iniciar sesión.";
                mensaje.style.color = "green";
            }
        }
    </script>
</body>
</html>
