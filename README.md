<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8" />
	<meta name="viewport" content="width=device-width,
					initial-scale=1.0" />
	<meta http-equiv="X-UA-Compatible" content="ie=edge" />
	<title>OTP Input</title>
	<style>
		.container {
			display: flex;
			justify-content: center;
			align-items: center;
			min-height: 100vh;
		}

		.input {
			width: 50px;
			border: none;
			border-bottom: 3px solid rgba(0, 0, 0, 0.5);
			margin: 0 10px;
			text-align: center;
			font-size: 36px;
			cursor: not-allowed;
			pointer-events: none;
		}

		.input:focus {
			border-bottom: 3px solid orange;
			outline: none;
		}

		.input:nth-child(1) {
			cursor: pointer;
			pointer-events: all;
		}
	</style>
</head>

<body>
	<div class="container">
		<div id="inputs" class="inputs">
			<input class="input" type="text" inputmode="numeric" maxlength="1" />
			<input class="input" type="text" inputmode="numeric" maxlength="1" />
			<input class="input" type="text" inputmode="numeric" maxlength="1" />
			<input class="input" type="text" inputmode="numeric" maxlength="1" />
		</div>
	</div>
	<script>
		const inputs = document.getElementById("inputs");

		inputs.addEventListener("input", function (e) {
			const target = e.target;
			const val = target.value;

			if (isNaN(val)) {
				target.value = "";
				return;
			}

			if (val != "") {
				const next = target.nextElementSibling;
				if (next) {
					next.focus();
				}
			}
		});

		inputs.addEventListener("keyup", function (e) {
			const target = e.target;
			const key = e.key.toLowerCase();

			if (key == "backspace" || key == "delete") {
				target.value = "";
				const prev = target.previousElementSibling;
				if (prev) {
					prev.focus();
				}
				return;
			}
		});
	</script>
</body>

</html>
