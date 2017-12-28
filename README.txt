//кліки за межі елементу
function clickOutside(e){
		if(!$(e.target).closest('.ourDiv').length){
			//do magic
		}
	}

****************************************************************************

//посилання на попередню сторінку
$('.link').on('click', function(e){
			parent.history.back();
			return false;
		});

****************************************************************************

# JS_Jquery
// неробить конфліктів jquery
1. var $= jQuery.noConflict();
2. jQuery(function ($) {}

****************************************************************************

//heigh 100vh for IOS
$('#hero').height(window.innerHeight + 'px');

*********************************************************************************

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
	
  *************************************************************
  
  //для Chorme в input type=date вказуємо сьогоднішню дату за замовчуванням
  document.getElementById('date').valueAsDate = new Date();
  
  *******************************************************************************
  
  // показуємо стрілку в гору, коли проскролили першу сторінку
	$(document).scroll(function() {
		var y = $(this).scrollTop();
		if (y < $(window).height()) {
			$('#toTop').css('display', 'none');
		} else {
			$('#toTop').css('display', 'block');
		}
	});

//smoose scroll to top
element.on('click', function(){
		$('body, html').animate({scrollTop: 0}, 300);
	});
**********************************************************************

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

*********************************************************************************

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
	
*********************************************************************************************	
	
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
    
    
 *********************************************************************   
 
 
//лічильник цифер (дів має мати клас .counter-value та атрибут data-count з числом до якого має рахувати лічильник)
//<span class="counter-value" data-count="5">0</span>
function counter(){
		var oTop = $('.integer').offset().top - window.innerHeight;
		if (a == 0 && $(window).scrollTop() > oTop) {
			$('.counter-value').each(function() {
				var $this = $(this),
				countTo = $this.attr('data-count');
				$({
					countNum: $this.text()
				}).animate({
					countNum: countTo
				},

				{
					duration: 2000,
					easing: 'swing',
					step: function() {
						$this.text(Math.floor(this.countNum));
					},
					complete: function() {
						$this.text(this.countNum);
					}
				});
			});
			a = 1;
		}
	}
	
*****************************************************

//slick slider включаємо, якщо стандартним способом вибиває помилку
$('.your-class').not('.slick-initialized').slick({})

***************************************************************

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
	
**********************************************************

//робиро фіксацію навігації, після проскролення його (додаємо клас active)
var nav = $('.navigation');
	$(document).scroll(function(){
		fixedNav();
	})

	$(window).resize(function(){
		fixedNav();
	})

	fixedNav();
	function fixedNav(){
		if($(window).width() > 767){
			var navHeight = nav.height();
			if($(this).scrollTop() > navHeight){
				nav.addClass('active');
			} else {
				nav.removeClass('active');
			}
		} else {
			nav.removeClass('active');
		}
	}

**********************************************************************************

//progress bar on slick slider
	var elem = $('#myBar');   
	var width = 1;
	var id = setInterval(progress, 40);
	function progress() {
		if (width >= 100) {
			width = 0;
			elem.css('width', width + '%');

			clearInterval(id);
			setTimeout(function(){
				id = setInterval(progress, 40);
			}, 1000)

		} else {
			width++;
			elem.css('width', width + '%');
		}
	}
	progress();

	$('.left-arrow, .right-arrow, .slick-arrow').on('click', function(){
		width = 0;
		elem.css('width', width + '%');
		clearInterval(id);
		id = setInterval(progress, 50);
			progress();	
	})
//html
<div id="myProgress">
		<div id="myBar"></div>
	</div>
//css
#myProgress{
		height: 10px;
		position: absolute;
		left: 0;
		width: 100%;
		border: 1px solid black;
		background-color: red;
		z-index: 50;
	}
	#myBar{
		height: 100%;
		width: 0;
		position: relative;
		background-color: black;
	}

**************************************************

//додаємо або забираємо клас в залежності в яку сторону скролим
//мій метод 
var lastScroll = 0;
	var currentScroll = 0;
	$(window).scroll(function(){
		currentScroll = $(this).scrollTop();
		console.log('current' + currentScroll);
		console.log('last position' + lastScroll);
		if($('body').scrollTop() > 500){

			if(lastScroll < currentScroll){
				$('.mainHeader').addClass('small');
			} else{
				$('.mainHeader').removeClass('small')
			}
			lastScroll = currentScroll;
		}
	})
	
//stackoverflow метод
	$(window).on( 'DOMMouseScroll mousewheel', function(event){
		if( event.originalEvent.detail > 0 || event.originalEvent.wheelDelta < 0 ){
			$('.mainHeader').addClass('small');
		} else {
			$('.mainHeader').removeClass('small')
		}
	});



*****************************************************************************************************************
при кліку на зображеня - відкриває пошту для відправки листа (замінник mailto:)
	$('.mailImg').on('click',function(event){
		event.preventDefault();
		var mail1 = 'info.',
		mail2 = 'w3@',
		mail3 = 'biospecimen-japan.com';
		window.location.href = 'mailto:'+mail1+mail2+mail3;
	});

****************************************************************************************************************

//плагін, який даєм можливість вибирати коди країн select (в форму вставляється)
http://www.jqueryscript.net/form/jQuery-International-Telephone-Input-With-Flags-Dial-Codes.html

****************************************************************************************************************

//задавати кастомний текст помилки на required атрибут
<input type="tel" placeholder="Phone:" id="tel" name="phone" required pattern=".{6,}" required oninvalid="setCustomValidity('Minimum length is 6 characters')"  oninput="setCustomValidity('')">

****************************************************************************************************************

//якщо каптча не відмічена - форму не відправляти
var captchResponse = $('#g-recaptcha-response').val();
if(captchResponse.length == 0 ){
			$('.captcha-err').fadeIn();
			return false;
		} else {
			return true;
		}


*******************************************************************************************************************

//parallax
$(window).scroll(function() {

	var st = $(this).scrollTop() /10;

	$(".object").css({
		"transform" : "translate3d(0px, " + st  + "%, .01px)",
		"-webkit-transform" : "translate3d(0px, " + st  + "%, .01px)"
	});

});

**********************************************************************************************************************

//play/pause video html5
var videoWr = $("#video-wr");
	var myVideo = document.getElementById("video"); 
	videoWr.on('click',function(){
		if(myVideo.paused){
			myVideo.play()
		} else{
			myVideo.pause();
		}
	})
	
**********************************************************************************************************************
	
//change image 
	function changeImg(){
		var img = El.attr('data-image');
		var imgSmall = El.attr('data-image-small');
		var windowWidth = $(window).width();
		
		if(windowWidth>995){
			El.css('background-image', 'url(' + img + ')');
		} else {
			El.css('background-image', 'url(' + imgSmall + ')');
		}
	}
	changeImg();
