q<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Biblioteca</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Biblioteca</h1>
        <form id="book-form">
            <input type="text" id="title" placeholder="Título do Livro" required>
            <input type="text" id="author" placeholder="Autor do Livro" required>
            <button type="submit">Adicionar Livro</button>
        </form>
        <h2>Lista de Livros</h2>
        <ul id="book-list"></ul>
    </div>
    <script src="scripts.js"></script>
</body>
</html>
document.getElementById('book-form').addEventListener('submit', function (e) {
    e.preventDefault();

    const title = document.getElementById('title').value;
    const author = document.getElementById('author').value;

    if (title !== '' && author !== '') {
        const li = document.createElement('li');
        li.appendChild(document.createTextNode(`${title} por ${author}`));

        const deleteBtn = document.createElement('button');
        deleteBtn.appendChild(document.createTextNode('Remover'));
        li.appendChild(deleteBtn);

        document.getElementById('book-list').appendChild(li);

        deleteBtn.addEventListener('click', function () {
            document.getElementById('book-list').removeChild(li);
        });

        document.getElementById('book-form').reset();
    }
});
