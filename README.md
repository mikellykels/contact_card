<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8">
	<meta name="description" content="Contact Card">
	<link rel="stylesheet" type="text/css" href="contactcard.css">
	<title>Contact Cards</title>
	<script type="text/javascript" src='http://code.jquery.com/jquery-1.10.2.min.js'></script> 
	<script type="text/javascript">
		$(document).ready(function(){
			$('form').submit(function(){
				var name = $('input[name="first_name"]').val() + ' ' + $('input[name="last_name"]').val();
				var dscr = $('textarea[name="description"]').val();
				$("#new_contact").append('<div class="contact"><h1 class="card">' + name + '</h1><h3 class="descr">' + dscr + '<h3 class="card">Click for description!</h3></div>');
				$('.card').show();
				$('.descr').hide();
				return false;
			});
			$('#new_contact').on('click', '.contact', function(){
				var front = $(this).children('h3').attr('style');
				var back;
				if (front == 'display: none;'){
				front = '.card';
				back = '.descr';
				} else {
				front = '.descr';
				back = '.card';
				};
					$(this).children(front).hide();
					$(this).children(back).show();
			});
		});
	</script>
</head>
<body>

	<div id="container">

		<div id="form">
			<form id="form1" action="process.php" method="post">
				<label>First Name:</label>
				<input class="firstname" type="text" placeholder="First Name" name="first_name">
				<label>Last Name:</label>
				<input class="lastname" type="text" placeholder="Last Name" name="last_name">
				<label>Description:</label>
				<textarea class="description" name="description" placeholder="Enter a description"></textarea>
				<input type="submit" value="Add Contact Card">
			</form>
		</div><!--end form-->

		<div id="new_contact">
		</div><!--end new_contact-->

	</div><!--end wrapper-->

</body>
</html>

