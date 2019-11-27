
<!DOCTYPE html>
<html>
<head>
	<title>login validation form</title>
	<link rel="stylesheet" type="text/css" href="css/login.css">
	<script src="https://use.fontawesome.com/29d51c6979.js"></script>
	<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js"></script>
	<script type="text/javascript">
	$(document).ready(function(){
		// set initially button state hidden
		$("#btn").hide();
		// use keyup event on email field
		$("#username").keyup(function(){
			if(validateEmail()){
				// if the email is validated
				// set input email border green
				$("#username").css("border","2px solid green");
				// and set label 
				$("#emailMsg").html("<p class='text-success'>vaid mail Id</p>");
			}
			else
			{
				// if the email is not validated
				// set border red
				$("#username").css("border","2px solid red");
				$("#emailMsg").html("<p class='text-danger'>Invalid mail id</p>");
			}
			buttonactive();
		});
		 
		$("#password").keyup(function(){
			// check
			if(validatePassword()){
				// set input password border green
				$("#password").css("border","2px solid green");
				//set passMsg 
				$("#passMsg").html("<p class='text-success'>Password validated</p>");
			}
			else
			{
					// set input password border red
				$("#password").css("border","2px solid red");
				//set passMsg 
				$("#passMsg").html("<p class='text-danger'>Password must contain atlest 8 characterstics</p>");
			}
			buttonactive();
		});
	});
	function buttonactive(){
		if(validateEmail() && validatePassword()){
			// if the both email and password are validate
			// then button should show visible
			$("#btn").show();
		}else{
			// if both email and pasword are not validated
			// button state should hidden
			$("#btn").hide();
		}
	}

	function validateEmail()
	{
		// get value of input email
		var email=$("#username").val();
		// use reular expression
		 var reg = /^\w+([-+.']\w+)@\w+([-.]\w+)\.\w+([-.]\w+)*$/
		 if(reg.test(email))
		 {
		 	return true;
		 }
		 else
		 {
		 	return false;
		 }
	}

	function validatePassword()
	{
		//get input password value
		var pass=$("#password").val();
		// check it s length
		if(pass.length > 7){
			return true;
		}else{
			return false;
		}
	}
</script>
</head>a
<body>
<div class="login-form">
	<div class="login-face">
		<img src="images/login.png">
	</div>
		<section class="form">
			<form>
				<div class="input">
					<input type="text" id="username" placeholder="enter the username" required>
					<i class="fa fa-user"></i>
					<span id="emailMsg"></span>
				</div>
				<div class="input">
					<input type="password" id="password" placeholder="enter your password" required>
					<i class="fa fa-lock"></i>
					<span id="passMsg"></span>
				</div>
				<a href="#" style="float: right;color: gray;font-size: 14px;text-decoration: none;margin-bottom: 10px;">Forget Password?</a>
				
					<p class="error-msg">Invalid Login details please check your credentials</p>
				<div class="input">
				<button class="btn btn-primary btn-block" id="btn">Submit</button>
			</div>
		</form>
	</section>
</div>
</body>
</html>
