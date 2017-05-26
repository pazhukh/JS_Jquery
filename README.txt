# JS_Jquery
// неробить конфліктів jquery
var $= jQuery.noConflict();

//heigh 100vh for IOS
$('#hero').height(window.innerHeight + 'px');

//add smooth scrolling, як параметри в душках вказуємо ті ссилки, якім треба додати ефект скролінгу
	$(".mainNav a, .heroTextWrap a, .gallerytSignUpFit a, #toTop").on('click', function(event) {
		if (this.hash !== "") {
			event.preventDefault();
			var hash = this.hash;
			$('html, body').animate({
				scrollTop: $(hash).offset().top
			}, 900);
		}
	});
  
  //для Chorme в input type=date вказуємо сьогоднішню дату за замовчуванням
  document.getElementById('date').valueAsDate = new Date();
  
  // показуємо стрілку в гору, коли проскролили першу сторінку
	$(document).scroll(function() {
		var y = $(this).scrollTop();
		if (y < $(window).height()) {
			$('#toTop').css('display', 'none');
		} else {
			$('#toTop').css('display', 'block');
		}
	});

//get date today
	var today = new Date();
	var dd = today.getDate();
	var mm = today.getMonth()+1; //January is 0!
	var yyyy = today.getFullYear();
	if(dd<10) {
	    dd='0'+dd
	} 
	if(mm<10) {
	    mm='0'+mm
	} 
	today = dd+'/'+ mm +'/'+yyyy;
	
//current year by Jquery
$("#year").text( (new Date).getFullYear() );



//додаємо різні переклади для Datapicker
$.datepicker.regional['uk'] = {
		closeText: 'Закрити',
		prevText: '&#x3c;Поп',
		nextText: 'Наст&#x3e;',
		currentText: 'Сьогодні',
		monthNames: ['Січень','Лютий','Березень','Квітень','Травень','Червень',
		'Липень','Серпень','Вересень','Жовтень','Листопад','Грудень'],
		monthNamesShort: ['Січ','Лют','Бер','Кві','Тра','Чер',
		'Лип','Сер','Вер','Жов','Лис','Гру'],
		dayNames: ['неділя','понеділок','вівторок','середа','четвер','пятниця','субота'],
		dayNamesShort: ['ндл','пнд','втр','срд','чтв','птн','сбт'],
		dayNamesMin: ['Нд','Пн','Вт','Ср','Чт','Пт','Сб'],
		dateFormat: 'dd.mm.yy',
		firstDay: 1,
		isRTL: false
	};
	$.datepicker.setDefaults($.datepicker.regional['uk']);
	
// fullpage.js якщо є частина на екнані, яка в нього не влазить, то при hover - відключається плагін, і можна прокрутити
$('.asideFull').hover(
		function(){
			//висота всього елементу
			var fullHeight = this.scrollHeight;
			//висота видимої області елементу
			var visbleHeight = this.offsetHeight;
			if(fullHeight > visbleHeight){
         		$.fn.fullpage.setMouseWheelScrolling(false); // якщо секція має overflow-відключаємо плагін
         	}
         }, function(){
     	 $.fn.fullpage.setMouseWheelScrolling(true); //включаємо плагін після забирання курсору з елемента
     	}
    );
    
//лічильник цифер до 100
var num = document.getElementById('num');
	var a = 0;
	var myNum = setInterval(number, 0.1);
	function number(){
		a++;
		num.innerText = a;
		if(a==100){
			clearInterval(myNum);
		}
	}

//slick slider включаємо, якщо стандартним способом вибиває помилку
$('.your-class').not('.slick-initialized').slick({})


//функція яка викликає alert в браузерах, в яких не підтримується required атрибут (при відправки форми)
$("form").submit(function(e) {
    	var ref = $(this).find("[required]");
	    $(ref).each(function(){
	        if ( $(this).val() == '' )
	        {
	            alert("Required field should not be blank.");
	            $(this).focus();
	            e.preventDefault();
	            return false;
	        }
	    });  return true;
	});


$(window).scroll(function(){
		var window_top = $(window).scrollTop() ; 
		var div_top = $('.nameClass').offset().top;
		if (window_top > div_top) {
			$('header').addClass('addClass');
		} else {
			$('header').removeClass('addClass');
		};
	});
/* 
.nameClass - який елемент має доторкнтутися
до верху екрану, щоб зробилися зміни з header
header - в який елемент будемо додавати класс
.addClass - клас, який будемо додавати до елемента
