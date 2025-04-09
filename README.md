# termo
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Jogo Termo</title>
  <style>
    body {
      font-family: sans-serif;
      background: #f0f0f0;
      text-align: center;
      padding: 40px;
    }
    .tentativas {
      margin-top: 20px;
    }
    .linha {
      display: flex;
      justify-content: center;
      margin-bottom: 10px;
    }
    .letra {
      width: 40px;
      height: 40px;
      margin: 2px;
      font-size: 24px;
      font-weight: bold;
      text-align: center;
      line-height: 40px;
      border-radius: 4px;
      background-color: #ccc;
    }
    .correta { background-color: #2ecc71; color: white; }
    .posicao-errada { background-color: #f1c40f; color: white; }
    .errada { background-color: #95a5a6; color: white; }
  </style>
</head>
<body>

  <h1>Jogo Termo</h1>
  <input type="text" id="entrada" maxlength="5" placeholder="Digite 5 letras" style="text-transform: uppercase; padding: 10px; font-size: 16px;" />
  <button id="btn">Tentar</button>

  <div class="tentativas" id="tentativas"></div>

  <script>
    const palavraSecreta = 'LIVRO';
    const btn = document.getElementById('btn');
    const entrada = document.getElementById('entrada');
    const tentativas = document.getElementById('tentativas');



    btn.addEventListener('click', () => {
      const tentativa = entrada.value.toUpperCase();
      if (tentativa.length !== 5) {
        alert('Digite exatamente 5 letras.');
        return;
      }

      const linha = document.createElement('div');
      linha.classList.add('linha');

      for (let i = 0; i < 5; i++) {
        const letra = document.createElement('div');
        letra.classList.add('letra');
        letra.textContent = tentativa[i];

        if (tentativa[i] === palavraSecreta[i]) {
          letra.classList.add('correta');
        } else if (palavraSecreta.includes(tentativa[i])) {
          letra.classList.add('posicao-errada');
        } else {
          letra.classList.add('errada');
        }

        linha.appendChild(letra);
      }

      tentativas.appendChild(linha);
      entrada.value = '';

      if (tentativa === palavraSecreta) {
        setTimeout(() => alert('Parabéns! Você acertou!'), 100);
      }
    });
  </script>

</body>
</html>
