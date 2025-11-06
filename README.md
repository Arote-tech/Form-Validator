<div class = "container">
            <form id = "registration-form">
                <h1>Register</h1>

                <div class = "form-group">
                    <label for="username">Username</label>
                    <input type="text" id = "username" placeholder = "Enter username">
                    <small></small>
                </div>

                <div class = "form-group">
                    <label for="email">Email</label>
                    <input type="email" id = "email" placeholder = "Enter email">
                    <small></small>
                </div>

                <div class = "form-group">
                    <label for="password">Password</label>
                    <input type="password" id = "password" placeholder = "Enter password">
                    <small></small>
                </div>

                <div class = "form-group">
                    <label for="confirmPassword">Confirm Password</label>
                    <input type="password" id = "confirmPassword" placeholder = "Confirm password">
                    <small></small>
                </div>

                <button type = "submit">Register</button>
            </form>
                            
        </div>

form.addEventListener("submit", function (e) {
    e.preventDefault();

    const isRequiredValid = checkRequired([username, email, password, confirmPassword ]);

    let isFormValid = isRequiredValid;

    if (isRequiredValid) {
        const isUsernameValid = checkLength(username, 3, 15);
        const isEmailValid = checkEmail(email);
        const isPasswordValid = checkLength(password, 6, 25);
        const isPasswordMatch = checkPasswordMatch(password, confirmPassword);


        isFormValid = isUsernameValid && isEmailValid && isPasswordValid && isPasswordMatch;
    }

    if (isFormValid) {
        alert("Registration successful");

        form.reset();

        document.querySelectorAll(".form-group").forEach(group => {
            group.className = "form-group";
        });
    }

})


body {
    background-color: #f9f9f9;
    font-family: sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
}

.container {
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0px 5px 15px rgba(0, 0, 0,0.1);
    width: 100%;
    max-width: 400px;
    padding: 30px;
    overflow: hidden;
}