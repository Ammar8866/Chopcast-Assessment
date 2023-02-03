<template>
<!-- ----------------------------Login template---------------------------- -->
<img class="wave" src="../assets/background.png">
<div class="main-container">
    <div class="Social-img">
        <h2 class ="usertext">User Image</h2>
        <div class="imagess" >
            <input v-model="image" id="imge">
        </div>
    </div>
    <div class="login-data">
        <form action="login.html">
            <img src="../assets/profile.png" id="picremove">
            <h2 class="title">User Profile</h2>
            <div class="input-div">
                <div class="i">
                    <i class="fas fa-user"></i>
                </div>
                <div class="div-1">
                    <input id="username" type="text" v-model="Firstname" class="input" placeholder="Firstname" autocomplete="off">
                </div>
            </div>
            <div class="input-div">
                <div class="i">
                    <i class="fas fa-user"></i>
                </div>
                <div class="div-1">
                    <input type="text" id="username" v-model="Lastname" class="input" placeholder="Lastname" autocomplete="off">
                </div>
            </div>
            <div class="input-div">
                <div class="i">
                    <i class="fas fa-user"></i>
                </div>
                <div class="div-1">
                    <input type="text" id="username" v-model="Email" class="input" placeholder="E-mail" autocomplete="off">
                </div>
            </div>
            <div class="input-div">
                <div class="i">
                    <i class="fas fa-lock"></i>
                </div>
                <div class="div-1">
                    <input type="password" id="password" v-model="password" class="input" placeholder="Password">
                </div>
            </div>
            <a href="#">Forgot Password?</a>

            <a class="btn" v-on:click="myBtn()">
                <p>SAVE</p>
            </a>
        </form>
    </div>
</div>
</template>

<script>
export default {
    name: 'Login',

    data() {
        return {
            Firstname: '',
            Lastname: '',
            Email: '',
            password: '',
            image: '',

        }
    },

    methods: {

        // ------------------------------------------Login Conditions----------------------------------

        async myBtn() {
            if (password.value !== "" && Firstname.value !== "") {
                try {
                    const arr = [];
                    const response = await fetch("https://dummyjson.com/auth/login", {
                        method: "POST",
                        headers: {
                            "Content-Type": "application/json"
                        },
                        body: JSON.stringify({
                            Firstname: this.Firstname /*---Jeanne---*/ ,
                            Lastname: this.Lastname /*---Halvorson---*/ ,
                            Email: this.Email /*---kminchelle@qq.com---*/ ,
                            password: this.password /*---0lelplR---*/ ,
                            image: this.image,

                        }),
                    });

                    if (response.status !== 400) {
                        console.log("success", response.status);
                        alert("Your Information is correct Data is Stored in Local Storage!");
                        // this.$router.push({
                        //     name: 'Cart'
                        // })
                    } else {
                        console.log("failed");
                        alert("Incorrect Details!");
                    }
                    arr.push({
                        Firstname: `Firstname is : ${Firstname.value}`
                    });
                    arr.push({
                        Lastname: `Lastname is : ${Lastname.value}`
                    });
                    arr.push({
                        Email: `Email is : ${Email.value}`
                    });
                    arr.push({
                        password: `password is : ${password.value}`
                    });
                    arr.push({
                        image: `image is : ${image.value}`
                    });
                    localStorage.setItem("", JSON.stringify(arr));
                } catch (error) {
                    console.log(error, "error");
                }
            } else {
                console.log("failed");
                alert("Please Enter Both field!");
            }
        },
    }
}
</script>

<style scoped>
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Poppins', sans-serif;
    overflow: hidden;
}

.imagess {
    height: 250px;
    width: 250px;
    border: 2px solid #ff0582;
    margin: 250px 120px 0px 4px;
}

.wave {
    position: fixed;
    bottom: 0;
    left: 0;
    height: 100%;
    width: 100%;
    z-index: -1;
    background-size: cover;

}

.main-container {
    width: 100vw;
    height: 100vh;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-gap: 7rem;
    padding: 0 2rem;
}

.Social-img {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    margin-bottom: 8rem;

}

#imge{
    width: 245px;
    height: 245px;
}
.usertext{
    margin:18px -213px 225px 0px;
    padding:115px 0px 0px 0px;
}

.login-data {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    text-align: center;
}

.Social-img img {
    width: 500px;
}

form {
    width: 360px;
}

.login-data img {
    height: 100px;
}

.login-data h2 {
    margin: 15px 0;
    color: rgb(0, 0, 0);
    text-transform: uppercase;
    font-size: 2.9rem;
}

.login-data .input-div {
    position: relative;
    display: grid;
    grid-template-columns: 7% 93%;
    margin: 25px 0;
    padding: 5px 0;
    border-bottom: 2px solid #000000;
}

.login-data .input-div {
    margin-top: 0;
}

.i {
    color: #000000;
    display: flex;
    justify-content: center;
    align-items: center;
}

.input-div>div>input {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    border: none;
    outline: none;
    background: none;
    padding: 0.5rem 2.7rem;
    font-size: 1.2rem;
    color: #000000;
    font-family: 'poppins', sans-serif;
}

a {
    display: block;
    text-align: right;
    text-decoration: none;
    color: rgb(0, 0, 0);
    font-size: 0.9rem;
    transition: .3s;
}

a:hover {
    color: #38d39f;
}

.btn {
    display: block;
    width: 100%;
    height: 50px;
    border-radius: 25px;
    outline: none;
    border: none;
    background-image: linear-gradient(to right, #0c1ec4, #38d39f, #0c1ec4);
    background-size: 200%;
    font-size: 1.2rem;
    color: #fff;
    font-family: 'Poppins', sans-serif;
    text-transform: uppercase;
    margin: 1rem 0;
    cursor: pointer;
    transition: .5s;

}

.btn p {
    align-items: center;
    padding: 15px 143px 0px 0px;
}

.btn:hover {
    background-position: right;
}

/* ------------------------------------MEDIA QUERIES RESPONSIVE-------------------------- */

@media screen and (max-width: 1050px) {
    .container {
        grid-gap: 5rem;
    }
}

@media screen and (max-width: 1000px) {
    form {
        width: 290px;
    }

    .login-content h2 {
        font-size: 2.4rem;
        margin: 8px 0;
    }

}

@media screen and (max-width: 900px) {
    .main-container {
        grid-template-columns: 1fr;
    }

    .img {
        display: none;
    }

    #picremove{
        display: none;
    }

    .login-data {
        justify-content: center;
    }

    .Social-img{
        margin: -85px -44px -125px 0px;
    }
}
</style>
