# para-pri
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>bom dia lindinha</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
        }
        img {
            max-width: 100%;
            height: auto;
            margin-top: 20px;
        }
        .question-container {
            margin-bottom: 20px;
        }
        .next-button {
            margin-top: 20px;
            display: none; /* Esconde o botão inicialmente */
        }
    </style>
</head>
<body>
    <h1>responda Pri</h1>
    <div id="question-container" class="question-container"></div>
    <div id="answer-container"></div>
    <button id="next-button" class="next-button" onclick="nextQuestion()">Próxima Pergunta</button>
    
    <script>
        const questions = [
            {
                question: 'voce prefere meus beijos ou meu abraço?',
                sim: {
                    text: 'aqui meus beijos',
                    image: 'beijo.jpg.jpg',
                    buttonText: 'beijos'
                },
                nao: {
                    text: 'aqui eles',
                    image: 'abraço.jpg',
                    buttonText: 'abraços'
                }
            },
            {
                question: 'oq vc mais gosta, a lua ou a chuva?',
                sim: {
                    text: 'deixa eu olhar ela com você',
                    image: 'lua.jpg',
                    buttonText: 'a lua'
                },
                nao: {
                    text: 'me deixa estar na chuva com você',
                    image: 'chuva.jpg',
                    buttonText: 'a chuva'
                }
            },
            {
                question: 'você gosta mais de Hotel Transilvania ou de Como treinar o seu Dragão?',
                sim: {
                    text: 'Aqui a gente',
                    image: 'hotel.jpg',
                    buttonText: 'Hotel transilvania'
                },
                nao: {
                    text: 'nós',
                    image: 'dragao.jpg',
                    buttonText: 'Como treinar o seu dragão'
                }
            },
            {
                question: 'namora cmg pra toda vida',
                sim: {
                    text: 'vou te fazer feliz fazendo computassao',
                    image: 'xonado.jpg',
                    buttonText: 'sim'
                },
                nao: {
                    text: 'ta bom, pelo menos tentei',
                    image: 'choro.jpg',
                    buttonText: 'não'
                }
            }
        ];

        let currentQuestion = 0;

        function showQuestion() {
            const questionContainer = document.getElementById('question-container');
            const current = questions[currentQuestion];
            questionContainer.innerHTML = `<p>${current.question}</p>
                                           <button onclick="handleAnswer('sim')">${current.sim.buttonText}</button>
                                           <button onclick="handleAnswer('nao')">${current.nao.buttonText}</button>`;
            document.getElementById('next-button').style.display = 'none'; // Esconde o botão "Próxima Pergunta"
        }

        function handleAnswer(answer) {
            const answerContainer = document.getElementById('answer-container');
            const response = questions[currentQuestion][answer];
            answerContainer.innerHTML = `<p>${response.text}</p><img src="${response.image}" alt="Imagem da resposta">`;
            document.getElementById('next-button').style.display = 'inline'; // Mostra o botão "Próxima Pergunta"
        }

        function nextQuestion() {
            const answerContainer = document.getElementById('answer-container');
            currentQuestion++;
            if (currentQuestion < questions.length) {
                answerContainer.innerHTML = '';  // Limpa a resposta anterior
                showQuestion();  // Mostra a próxima pergunta
            } else {
                answerContainer.innerHTML = '<p>eu quero você</p>';
                document.getElementById('next-button').style.display = 'none'; // Esconde o botão ao fim das perguntas
            }
        }

        // Mostra a primeira pergunta ao carregar a página
        showQuestion();
    </script>
</body>
</html>
