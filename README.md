const questions = [
  {
    question: 'ما هو لونك المفضل؟',
    answers: [
      { text: 'أحمر', score: 3 },
      { text: 'أزرق', score: 1 },
      { text: 'أخضر', score: 2 },
      { text: 'أصفر', score: 4 },
    ]
  },
  {
    question: 'ما هو حيوانك المفضل؟',
    answers: [
      { text: 'قط', score: 1 },
      { text: 'كلب', score: 3 },
      { text: 'طائر', score: 2 },
      { text: 'سمكة', score: 4 },
    ]
  }
  // يمكنك إضافة المزيد من الأسئلة هنا
];

let currentQuestionIndex = 0;
let totalScore = 0;

function showQuestion() {
  const questionElement = document.getElementById('question');
  const answersElement = document.getElementById('answers');
  const currentQuestion = questions[currentQuestionIndex];

  questionElement.textContent = currentQuestion.question;
  answersElement.innerHTML = '';

  currentQuestion.answers.forEach(answer => {
    const button = document.createElement('button');
    button.textContent = answer.text;
    button.onclick = () => selectAnswer(answer.score);
    answersElement.appendChild(button);
  });
}

function selectAnswer(score) {
  totalScore += score;
  currentQuestionIndex++;

  if (currentQuestionIndex < questions.length) {
    showQuestion();
  } else {
    showResult();
  }
}

function showResult() {
  const quizContainer = document.getElementById('quiz-container');
  const resultContainer = document.getElementById('result');
  const resultText = document.getElementById('result-text');

  let resultMessage;
  if (totalScore < 8) {
    resultMessage = 'شخصية هادئة ومسالمة';
  } else if (totalScore < 12) {
    resultMessage = 'شخصية متوازنة';
  } else {
    resultMessage = 'شخصية نشطة ومفعمة بالحيوية';
  }

  resultText.textContent = resultMessage;
  quizContainer.classList.add('hidden');
  resultContainer.classList.remove('hidden');
}

function resetQuiz() {
  currentQuestionIndex = 0;
  totalScore = 0;
  const quizContainer = document.getElementById('quiz-container');
  const resultContainer = document.getElementById('result');

  quizContainer.classList.remove('hidden');
  resultContainer.classList.add('hidden');
  showQuestion();
}

showQuestion();
# Personality_quiz
