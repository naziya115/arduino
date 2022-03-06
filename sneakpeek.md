# Sneak Peek TO-DO List for 06.03.
### Gotta finish translation for all pages:

- ~~school level tests translation everywhere~~
- review page translation
- register translation 

- my tests main page and review location
- links in Log In and Register + btns translation

- link to main page in school level through Sneak Peek



Review First code
```
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Review</title>

<!-- Stylesheet -->
<link rel="stylesheet" href="review_style.css" />
<link rel="stylesheet" href="additionalCSS/text_style.css">
<link rel="stylesheet" href="additionalCSS/tests_style.css">
<link rel="stylesheet" href="additionalCSS/dark_mode_style.css">
</head>
<body>
<!--Header with user name, sign up button, and divider between them-->
<div id = "head" class="header boxShadow">
   <svg id = "websiteIcon" xmlns="http://www.w3.org/2000/svg" width="30" height="30" fill="currentColor" class="bi bi-bookmark-heart" viewBox="0 0 16 16">
     <path fill-rule="evenodd" d="M8 4.41c1.387-1.425 4.854 1.07 0 4.277C3.146 5.48 6.613 2.986 8 4.412z"/>
     <path d="M2 2a2 2 0 0 1 2-2h8a2 2 0 0 1 2 2v13.5a.5.5 0 0 1-.777.416L8 13.101l-5.223 2.815A.5.5 0 0 1 2 15.5V2zm2-1a1 1 0 0 0-1 1v12.566l4.723-2.482a.5.5 0 0 1 .554 0L13 14.566V2a1 1 0 0 0-1-1H4z"/>
   </svg>
   <b id = "WebSite_Name">Sneak Peek</b>
  <div align = "center" id = "mytests"><a href = "school_level.jsp" onclick = "tests()"  class = "underlineTests" id = "testLink">My Tests</a></div>
 </div>

<div class="container">
 <div class="row">
    <col-1>
      <h1 id = "resultstxt">Results of the Practice Test</h1>
      <div class="alert alert-success">
         Great Job! Make a quick review after taking the test and make sure you learn from your mistakes.
      </div>
      <!--Pretty button to show review scrollspy-->
      <button type="button" onclick = "show()" id = "reviewbtn" class="reviewbtn">Review</button>
   </col-1>
    <col-2>
    <div class="content">
      <div class="circular-progress">
      <div class="value-container">0%</div></div>
      </div>
   </col-2>
 </div>
</div>

    <!-- Review option --> 
<div id = "review">
   <div class="row mt-5">
      <div class="col-lg-4 left-content">
         <div class="sidebar navbar">
            <h5 id = "sidebar-title">Menu</h5>
            <p class = "navpills" id = "navpill1"><a href="#task1">Task1</a></p>
            <p class = "navpills" id = "navpill2"><a href="#task2">Task2</a></p>
            <p class = "navpills" id = "navpill3"><a href="#task3">Taks3</a></p>
            <p class = "navpills" id = "navpill4"><a href="#task4">Task4</a></p>
            <p class = "navpills" id = "navpill5"><a href="#task5">Task5</a></p>
         </div>
      </div>
 <div class="col-lg-6 right-content review">
   <div data-spy="scroll" data-target="#navbar-example3" data-offset="0" class="nav-desc">
      <h3 id="titleOftheTest">CS</h3>
         <p id = "description"></p>
            <h5 id="task1" class = "titleOftheTest"><strong>Task 1-1</strong></h5>
         <p id = "ex1"></p>
            <h5 id="task2" class = "titleOftheTest"><strong>Task 1-2</strong></h5>
         <p id = "ex2"></p>
            <h5 id="task3" class = "titleOftheTest"><strong>Task 2-1</strong></h5>
         <p id = "ex3"></p>
            <h5 id="task4" class = "titleOftheTest"><strong>Task 3-1</strong></h5>
         <p id = "ex4"></p>
            <h5 id="task5" class = "titleOftheTest"><strong>Task 3-2</strong></h5>
         <p id = "ex5"></p>
   </div>
</div>
</div>
</div>


 <!-- Script-->
 <script src="review_script.js"></script>
<script src = "additionalCSS/darktests_script.js"></script>

<script>
alert(localStorage.getItem("lang"));
if(localStorage.getItem("lang") === "kaz"){
	alert(localStorage.getItem("lang"));
	//changetoKaz();
}else if(localStorage.getItem("lang") === "rus"){
	//changetRus();
}

function changetoKaz(){
	/*const resultstxt = document.querySelectorAll('#resultstxt');
	resultstxt.textContent = "Практикалық тест нәтижелері";
	alert(resultstxt.textContent);*/
	/*const alert = document.querySelector('.alert');
	const reviewbtn = document.querySelector('#reviewbtn');
	const sidebar-title = document.querySelector('.sidebar-title');
	const navpill1 = document.querySelector('#navpill1');
	const navpill2 = document.querySelector('#navpill2');
	const navpill3 = document.querySelector('#navpill3');
	const navpill4 = document.querySelector('#navpill4');
	const navpill5 = document.querySelector('#navpill5');*/
	

/*	alert.textContent = "Керемет Жұмыс! Тесттен өткеннен кейін қысқаша шолу жасаңыз және қателіктеріңізден сабақ алғаныңызға көз жеткізіңіз.";
	reviewbtn.textContent = "Шолу";
	sidebar-title.textContent = "Меню";
	navpill1.textContent = "1—тапсырма";
	navpill2.textContent = "2—тапсырма";
	navpill3.textContent = "3—тапсырма";
	navpill4.textContent = "4—тапсырма";
	navpill5.textContent = "5—тапсырма";*/
}
function changetoRus(){
	const resultstxt = document.querySelectorAll('#resultstxt');
	const alert = document.querySelector('.alert');
	const reviewbtn = document.querySelector('#reviewbtn');
	const sidebar-title = document.querySelector('.sidebar-title');
	const navpill1 = document.querySelector('#navpill1');
	const navpill2 = document.querySelector('#navpill2');
	const navpill3 = document.querySelector('#navpill3');
	const navpill4 = document.querySelector('#navpill4');
	const navpill5 = document.querySelector('#navpill5');
	
	resultstxt.textContent = "Результаты практического теста";
	alert.textContent = "Отличная работа! После прохождения теста сделайте быстрый обзор и убедитесь, что вы учитесь на своих ошибках.";
	reviewbtn.textContent = "Обзор";
	sidebar-title.textContent = "Меню";
	navpill1.textContent = "1—задание";
	navpill2.textContent = "2—задание";
	navpill3.textContent = "3—задание";
	navpill4.textContent = "4—задание";
	navpill5.textContent = "5—задание";
	
}
</script>
 
</body>
</html>
```
