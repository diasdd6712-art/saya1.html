```html
<!DOCTYPE html>
<html lang="kk">
<head>
<meta charset="UTF-8">
<title>Тест қосымшасы</title>

<style>

body{
font-family: Arial;
background: linear-gradient(135deg,#4facfe,#00f2fe);
height:100vh;
display:flex;
align-items:center;
justify-content:center;
margin:0;
}

.container{
background:white;
width:400px;
padding:30px;
border-radius:15px;
box-shadow:0 10px 25px rgba(0,0,0,0.2);
text-align:center;
}

h1{
color:#333;
}

.question{
font-size:20px;
margin:20px 0;
}

.answers button{
display:block;
width:100%;
margin:10px 0;
padding:12px;
border:none;
border-radius:8px;
background:#4facfe;
color:white;
font-size:16px;
cursor:pointer;
transition:0.3s;
}

.answers button:hover{
background:#00c6ff;
transform:scale(1.05);
}

#nextBtn{
margin-top:20px;
padding:10px 20px;
border:none;
border-radius:8px;
background:#00c853;
color:white;
font-size:16px;
cursor:pointer;
display:none;
}

.result{
font-size:22px;
color:#333;
}

</style>
</head>

<body>

<div class="container">

<h1>Тест</h1>

<div id="quiz">

<div class="question" id="question"></div>

<div class="answers" id="answers"></div>

<button id="nextBtn">Келесі</button>

</div>

<div class="result" id="result"></div>

</div>

<script>

const questions = [

{
question:"Python қандай тіл?",
answers:["Бағдарламалау тілі","Ойын","Сайт","Операциялық жүйе"],
correct:0
},

{
question:"HTML не үшін қолданылады?",
answers:["Дизайн","Сайт жасау","Ойын жасау","Видео монтаж"],
correct:1
},

{
question:"CSS не істейді?",
answers:["Сайттың стилін жасайды","Код жазады","Музыка қосады","Видео көрсетеді"],
correct:0
},

{
question:"JavaScript не үшін керек?",
answers:["Сайтқа логика қосу","Фото салу","Музыка жазу","Файл сақтау"],
correct:0
},

{
question:"Android қосымша қай жерде жасалады?",
answers:["Android Studio","Word","Paint","Excel"],
correct:0
}

];

let currentQuestion=0;
let score=0;

const question=document.getElementById("question");
const answers=document.getElementById("answers");
const nextBtn=document.getElementById("nextBtn");
const result=document.getElementById("result");

function showQuestion(){

answers.innerHTML="";
nextBtn.style.display="none";

let q=questions[currentQuestion];
question.innerText=q.question;

q.answers.forEach((answer,index)=>{

let btn=document.createElement("button");
btn.innerText=answer;

btn.onclick=()=>{

if(index===q.correct){
score++;
}

nextBtn.style.display="block";

};

answers.appendChild(btn);

});

}

nextBtn.onclick=()=>{

currentQuestion++;

if(currentQuestion<questions.length){

showQuestion();

}else{

document.getElementById("quiz").style.display="none";

result.innerHTML="Сіздің нәтиже: "+score+" / "+questions.length;

}

};

showQuestion();

</script>

</body>
</html>
```
