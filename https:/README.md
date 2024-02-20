```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Meu Cronômetro de Objetivos</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="tabs">
    <button class="tablinks" onclick="openTab(event, 'alura')">Curso Alura</button>
    <button class="tablinks" onclick="openTab(event, 'projeto')">Criar Projeto em JavaScript</button>
    <button class="tablinks" onclick="openTab(event, 'portfolio')">Criar Portfólio</button>
    <button class="tablinks" onclick="openTab(event, 'curriculo')">Atualizar Meu Currículo</button>
  </div>

  <div id="alura" class="tabcontent">
    <h3>Tempo para terminar o objetivo: <span id="cronometroAlura">0d 00:00:00</span></h3>
  </div>

  <!-- Adicione os outros blocos de conteúdo semelhantes para os outros objetivos -->

  <script src="script.js"></script>
</body>
</html>
```
```css
body {
  font-family: Arial, sans-serif;
  background-color: #f2f2f2;
}

.tabs {
  text-align: center;
  margin-top: 20px;
}

.tablinks {
  background-color: #4CAF50; /* cor de fundo das abas */
  color: white;
  padding: 14px 16px;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s;
}

.tablinks:hover {
  background-color: #45a049; /* cor de fundo das abas ao passar o mouse */
}

.tabcontent {
  display: none;
}

#alura {background-color: #007777;} /* cor de fundo da aba alura */
#projeto {background-color: #0066cc;} /* cor de fundo da aba projeto */
#portfolio {background-color: #6600cc;} /* cor de fundo da aba portfolio */
#curriculo {background-color: #cc0099;} /* cor de fundo da aba curriculo */

h3 {
  color: white; /* cor do texto "Tempo para terminar o objetivo" */
}

#cronometroAlura {
  color: #4CAF50; /* cor dos números do cronômetro alura */
}
```
```javascript
// Função para formatar o tempo em dias, horas, minutos e segundos
function formatTime(seconds) {
  const days = Math.floor(seconds / (3600 * 24));
  const hours = Math.floor((seconds % (3600 * 24)) / 3600);
  const minutes = Math.floor((seconds % 3600) / 60);
  const remainingSeconds = seconds % 60;
  
  return `${days}d ${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${remainingSeconds.toString().padStart(2, '0')}`;
}

// Função para iniciar o cronômetro
function startTimer(elementId, totalSeconds) {
  const element = document.getElementById(elementId);
  
  let currentSeconds = totalSeconds;
  
  function updateTimer() {
    element.textContent = formatTime(currentSeconds);
    currentSeconds--;
    
    if (currentSeconds < 0) {
      clearInterval(timerInterval);
      element.textContent = 'Tempo esgotado!';
    }
  }
  
  updateTimer();
  const timerInterval = setInterval(updateTimer, 1000); // Atualiza o cronômetro a cada segundo
}

// Iniciar os cronômetros para cada objetivo
startTimer('cronometroAlura', 259200); // Exemplo de 3 dias (259200 segundos)
// Adicione as chamadas startTimer para os outros objetivos aqui
``` 
