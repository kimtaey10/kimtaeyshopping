<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BASEBALL PRO - 야구 전문 쇼핑몰</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Arial', sans-serif;
    background: #f5f6f8;
    color: #222;
}

header {
    background: #102b24;
    color: white;
    padding: 22px 7%;
}

.header-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 15px;
}

.logo {
    font-size: 29px;
    font-weight: bold;
    color: #f4c542;
}

.header-menu a {
    color: white;
    text-decoration: none;
    margin-left: 20px;
    font-size: 14px;
}

.search {
    margin-top: 20px;
    display: flex;
}

.search input {
    width: 100%;
    padding: 13px;
    border: none;
    border-radius: 5px 0 0 5px;
}

.search button {
    background: #e6b938;
    border: none;
    padding: 13px 25px;
    cursor: pointer;
    font-weight: bold;
}

nav {
    background: white;
    padding: 17px;
    text-align: center;
    border-bottom: 1px solid #ddd;
}

nav button {
    background: none;
    border: none;
    margin: 0 20px;
    font-size: 16px;
    font-weight: bold;
    cursor: pointer;
}

nav button:hover {
    color: #c28d16;
}

.hero {
    background: linear-gradient(110deg, #102b24, #315b43);
    color: white;
    padding: 65px 8%;
    text-align: center;
}

.hero h1 {
    font-size: 38px;
    margin-bottom: 15px;
}

.hero p {
    font-size: 17px;
    color: #e2e8df;
}

.container {
    max-width: 1200px;
    margin: 40px auto;
    padding: 0 20px;
}

.section-title {
    font-size: 25px;
    margin-bottom: 25px;
}

.benefit {
    background: white;
    padding: 25px;
    border-radius: 12px;
    margin-bottom: 45px;
    box-shadow: 0 3px 12px #0000000b;
}

.benefit h2 {
    margin-bottom: 20px;
    color: #173e2d;
}

.grade-list {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 12px;
}

.grade {
    text-align: center;
    padding: 22px 10px;
    border-radius: 9px;
    background: #f4f5f6;
}

.grade h3 {
    margin-bottom: 10px;
}

.grade strong {
    font-size: 27px;
    color: #b48b27;
}

.grade p {
    font-size: 13px;
    margin-top: 8px;
    color: #666;
}

.customer-box {
    background: #fff;
    padding: 25px;
    border-radius: 12px;
    margin-bottom: 45px;
}

.customer-box input {
    padding: 12px;
    width: 220px;
    border: 1px solid #ddd;
    border-radius: 5px;
    margin: 12px 5px 12px 0;
}

.customer-box button {
    background: #173e2d;
    color: white;
    border: none;
    padding: 13px 22px;
    border-radius: 5px;
    cursor: pointer;
}

#gradeResult {
    margin-top: 15px;
    line-height: 1.8;
    color: #173e2d;
    font-weight: bold;
}

.product-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
}

.product {
    background: white;
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 3px 10px #0000000b;
}

.product img {
    width: 100%;
    height: 190px;
    object-fit: cover;
    background: #eee;
}

.product-info {
    padding: 17px;
}

.product-info h3 {
    font-size: 17px;
    margin-bottom: 10px;
}

.price {
    font-weight: bold;
    font-size: 19px;
    color: #b38a25;
    margin-bottom: 15px;
}

.product button {
    width: 100%;
    padding: 12px;
    border: none;
    background: #173e2d;
    color: white;
    border-radius: 5px;
    cursor: pointer;
}

.product button:hover {
    background: #286447;
}

.cart {
    background: #fff;
    padding: 20px;
    margin-top: 40px;
    border-radius: 10px;
}

footer {
    background: #102b24;
    color: white;
    text-align: center;
    padding: 35px;
    margin-top: 60px;
    line-height: 2;
}

@media(max-width:800px) {
    .product-grid {
        grid-template-columns: repeat(2, 1fr);
    }
    .grade-list {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media(max-width:480px) {
    .product-grid {
        grid-template-columns: 1fr;
    }
    .hero h1 {
        font-size: 27px;
    }
}
</style>
</head>

<body>

<header>
    <div class="header-top">
        <div class="logo">⚾ BASEBALL PRO</div>
        <div class="header-menu">
            <a href="#">로그인</a>
            <a href="#">회원가입</a>
            <a href="#cart">장바구니 🛒 <span id="cartCount">0</span></a>
        </div>
    </div>

    <div class="search">
        <input type="text" id="searchInput"
        placeholder="원하는 야구용품을 검색하세요">
        <button onclick="searchProducts()">검색</button>
    </div>
</header>

<nav>
    <button onclick="filterProducts('all')">전체상품</button>
    <button onclick="filterProducts('pitcher')">투수용품</button>
    <button onclick="filterProducts('batter')">타자용품</button>
    <button onclick="document.getElementById('benefit').scrollIntoView()">회원혜택</button>
</nav>

<section class="hero">
    <h1>YOUR BASEBALL, YOUR BEST</h1>
    <p>야구를 사랑하는 당신을 위한 최고의 야구 전문 쇼핑몰</p>
    <p style="margin-top:20px;color:#f4c542;">
        투수부터 타자까지, 최고의 장비를 만나보세요!
    </p>
</section>

<div class="container">

    <section class="benefit" id="benefit">
        <h2>🏆 회원 등급별 특별 적립 혜택</h2>
        <p style="margin-bottom:20px;color:#666;">
            연간 구매금액에 따라 더 큰 혜택을 드립니다!
        </p>

        <div class="grade-list">
            <div class="grade">
                <h3>일반 회원</h3>
                <strong>0%</strong>
                <p>10만원 미만</p>
            </div>

            <div class="grade">
                <h3>브론즈</h3>
                <strong>1%</strong>
                <p>10만원 이상</p>
            </div>

            <div class="grade">
                <h3>실버</h3>
                <strong>3%</strong>
                <p>30만원 이상</p>
            </div>

            <div class="grade">
                <h3>골드</h3>
                <strong>5%</strong>
                <p>50만원 이상</p>
            </div>
        </div>
    </section>

    <section class="customer-box">
        <h2>💎 나의 회원 등급 확인</h2>
        <p style="margin-top:10px;color:#666;">
            올해 누적 구매금액을 입력하면 적립률을 확인할 수 있습니다.
        </p>

        <input type="number" id="annualPurchase"
        placeholder="연간 구매금액 입력">

        <button onclick="checkGrade()">등급 확인</button>

        <div id="gradeResult"></div>
    </section>

    <h2 class="section-title" id="productTitle">
        ⚾ 인기 야구용품
    </h2>

    <div class="product-grid" id="productList"></div>

    <section class="cart" id="cart">
        <h2>🛒 장바구니</h2>
        <div id="cartItems" style="margin-top:15px;">
            장바구니가 비어 있습니다.
        </div>
        <h3 id="totalPrice" style="margin-top:20px;">
            총 금액: 0원
        </h3>
    </section>

</div>

<footer>
    <h2>⚾ BASEBALL PRO</h2>
    <p>야구를 사랑하는 모든 사람들을 위한 쇼핑몰</p>
    <p>고객센터 : 1588-0000</p>
    <p>Copyright © 2026 BASEBALL PRO. All Rights Reserved.</p>
</footer>

<script>

const products = [
    {
        name:"야구 글러브",
        category:"pitcher",
        price:89000,
        image:"https://placehold.co/400x300/eeeeee/333333?text=BASEBALL+GLOVE"
    },
    {
        name:"투수용 스파이크",
        category:"pitcher",
        price:120000,
        image:"https://placehold.co/400x300/eeeeee/333333?text=PITCHER+SPIKES"
    },
    {
        name:"투수 연습용 공",
        category:"pitcher",
        price:15000,
        image:"https://placehold.co/400x300/eeeeee/333333?text=BASEBALL"
    },
    {
        name:"투수용 로진백",
        category:"pitcher",
        price:12000,
        image:"https://placehold.co/400x300/eeeeee/333333?text=ROSIN+BAG"
    },
    {
        name:"알루미늄 야구 배트",
        category:"batter",
        price:135000,
        image:"https://placehold.co/400x300/eeeeee/333333?text=BASEBALL+BAT"
    },
    {
        name:"타자용 배팅 장갑",
        category:"batter",
        price:35000,
        image:"https://placehold.co/400x300/eeeeee/333333?text=BATTING+GLOVES"
    },
    {
        name:"타자용 헬멧",
        category:"batter",
        price:48000,
        image:"https://placehold.co/400x300/eeeeee/333333?text=BATTING+HELMET"
    },
    {
        name:"타자용 보호대",
        category:"batter",
        price:55000,
        image:"https://placehold.co/400x300/eeeeee/333333?text=BATTER+GUARD"
    }
];

let cart = [];

function displayProducts(list) {
    const area = document.getElementById("productList");

    area.innerHTML = "";

    list.forEach((product) => {
        const index = products.indexOf(product);

        area.innerHTML += `
            <div class="product">
                <img src="${product.image}"
                alt="${product.name}">
                <div class="product-info">
                    <h3>${product.name}</h3>
                    <div class="price">
                    ${product.price.toLocaleString()}원
                    </div>
                    <button onclick="addCart(${index})">
                    장바구니 담기
                    </button>
                </div>
            </div>
        `;
    });
}

function filterProducts(category) {
    let filtered;

    if(category === "all") {
        filtered = products;
        document.getElementById("productTitle").innerText =
        "⚾ 인기 야구용품";
    } else {
        filtered = products.filter(
            p => p.category === category
        );

        document.getElementById("productTitle").innerText =
        category === "pitcher" ?
        "⚾ 투수 전용 용품" : "⚾ 타자 전용 용품";
    }

    displayProducts(filtered);
}

function searchProducts() {
    const keyword =
    document.getElementById("searchInput").value;

    const result = products.filter(p =>
        p.name.includes(keyword)
    );

    displayProducts(result);
    document.getElementById("productTitle").innerText =
    "🔎 검색 결과";
}

function addCart(index) {
    cart.push(products[index]);
    updateCart();
}

function updateCart() {
    const area = document.getElementById("cartItems");
    const count = document.getElementById("cartCount");

    count.innerText = cart.length;

    if(cart.length === 0) {
        area.innerText = "장바구니가 비어 있습니다.";
        document.getElementById("totalPrice").innerText =
        "총 금액: 0원";
        return;
    }

    let total = 0;

    area.innerHTML = cart.map((item, index) => {
        total += item.price;

        return `
            <p style="margin-bottom:10px;">
            ${item.name} - ${item.price.toLocaleString()}원
            <button onclick="removeCart(${index})"
            style="margin-left:10px;">삭제</button>
            </p>
        `;
    }).join("");

    document.getElementById("totalPrice").innerText =
    "총 금액: " + total.toLocaleString() + "원";
}

function removeCart(index) {
    cart.splice(index, 1);
    updateCart();
}

function checkGrade() {
    const amount = Number(
        document.getElementById("annualPurchase").value
    );

    let grade = "일반 회원";
    let rate = 0;

    if(amount >= 500000) {
        grade = "골드 회원";
        rate = 5;
    } else if(amount >= 300000) {
        grade = "실버 회원";
        rate = 3;
    } else if(amount >= 100000) {
        grade = "브론즈 회원";
        rate = 1;
    }

    const point = Math.floor(amount * rate / 100);

    document.getElementById("gradeResult").innerHTML = `
        회원 등급 : ${grade}<br>
        현재 적립률 : ${rate}%<br>
        예상 적립 포인트 : ${point.toLocaleString()}P
    `;
}

displayProducts(products);

</script>

</body>
</html>
# kimtaeyshopping
1119 shopping mall
