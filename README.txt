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
