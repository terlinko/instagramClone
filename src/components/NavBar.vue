<template>
    <nav>
        <div class="navitems">
            <div class="logo">
                <router-link to="/"><img src="https://www.pngkey.com/png/full/28-287308_instagram-logo-text-white.png"></router-link>
            </div>
            <ul class="mainitems">
                <li class="item">
                    <router-link to="/"> <i class="fa-solid fa-house"></i> 홈</router-link>
                </li>
                <li class="item">
                    <a><i class="fa-solid fa-magnifying-glass"></i> 검색</a>
                </li>
                <li class="item">
                    <router-link to="/empty"><i class="fa-regular fa-compass"></i> 탐색 탭</router-link>
                </li>
                <li class="item">
                    <router-link to="/empty"><i class="fa-solid fa-clapperboard"></i> 릴스</router-link>
                </li>
                <li class="item">
                    <router-link to="/dm"><i class="fa-regular fa-paper-plane"></i> 메시지</router-link>
                </li>
                <li class="item">
                    <a><i class="fa-regular fa-heart"></i> 알림</a>
                    <!-- <i class="fa-solid fa-heart"></i> 꽉찬 하트 -->
                </li>
                <li class="item">
                    <a><i class="fa-regular fa-square-plus"></i> 만들기</a>
                </li>
                <li class="item">
                    <router-link to="/empty"><i class="fa-solid fa-circle"></i> 프로필</router-link>
                    <!-- i 대신 프로필 이미지 들어가야함 -->
                </li>
            </ul>
            <br>
            <div class="item" id="showmore">
                <a><i class="fa-solid fa-bars"></i> 더 보기</a>
            </div>
            
        </div>
    </nav>
</template>

<script>
export default {

}
</script>

<style>
nav{
    float: left;
    position: fixed;
    background-color: black;
    font-size: large;
    /* padding: 30px; */
    height: 100vh;
    /* display: flex; */
    justify-content: space-between;
    border-right: 0.1px rgb(68, 68, 68) solid;
}
nav a {
    box-sizing: border-box;
    color: whitesmoke;
    text-decoration: none;
    /* margin-bottom: 130px; */
    
}

nav a.router-link-exact-active {
    color: white;
    font-weight: bold;
}
.mainitems{
    list-style: none;
    padding: 0;
}
.logo{
    position: relative;
    padding-top: 40px;
    padding-left: 25px;
    padding-bottom: 30px;
    height: 30px;
    width: 105px;
    padding-right: 100px;
}
.logo img{
    
    width: 100%;
    /* -webkit-filter: opacity(.5) drop-shadow(0 0 0 white);
    filter: opacity(.5) drop-shadow(0 0 0 white);; */
}
.item{
    /* padding-bottom: 30px; */
    padding: 10px;
}
#showmore{
    
    /* padding-right: 300px; */
    position: absolute;
    bottom: 10px;
}
.item a{
    display: inline-block;
    box-sizing: border-box;
    width: 200px;
    /* height: 30px; */
    padding-top: 5px;
    padding-bottom: 5px;
    padding-left: 5px;
    padding-right: 5px;
    cursor: pointer;

}
.item a:hover{
    border-radius: 15px;
    background-color: rgb(26, 26, 26);
}

</style>