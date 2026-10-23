Lưu toàn bộ phần code dưới đây vào một file tên "index.html".

<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Săn Deal Giá Tốt - Mua sắm thông minh</title>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial, sans-serif;
    background: #f5f6fa;
    color: #222;
}

header {
    background: #ee3045;
    color: white;
    padding: 22px 15px;
    text-align: center;
}

header h1 {
    font-size: 28px;
    margin-bottom: 8px;
}

header p {
    font-size: 14px;
}

.search-box {
    max-width: 600px;
    margin: 18px auto 0;
    display: flex;
    gap: 8px;
}

.search-box input {
    flex: 1;
    min-width: 0;
    padding: 12px;
    border: none;
    border-radius: 8px;
    font-size: 15px;
}

.search-box button {
    border: none;
    border-radius: 8px;
    padding: 12px 16px;
    background: #ffcf33;
    font-weight: bold;
    cursor: pointer;
}

nav {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 10px;
    background: white;
    padding: 14px 8px;
}

nav button {
    padding: 9px 13px;
    border: 1px solid #eee;
    border-radius: 20px;
    background: white;
    cursor: pointer;
}

nav button:hover {
    background: #ffe6e9;
}

.banner {
    margin: 18px auto;
    max-width: 1100px;
    padding: 25px 15px;
    background: linear-gradient(120deg, #ff304b, #ff8a45);
    color: white;
    text-align: center;
    border-radius: 12px;
}

.banner h2 {
    margin-bottom: 8px;
}

.container {
    max-width: 1100px;
    margin: auto;
    padding: 0 12px 25px;
}

.section-title {
    margin: 25px 0 15px;
    font-size: 22px;
}

.products {
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr));
    gap: 14px;
}

.product {
    background: white;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 2px 8px #0000000c;
    display: flex;
    flex-direction: column;
}

.product img {
    width: 100%;
    aspect-ratio: 1 / 1;
    object-fit: cover;
    background: #eee;
}

.product-info {
    padding: 12px;
    display: flex;
    flex-direction: column;
    flex: 1;
}

.product h3 {
    font-size: 15px;
    line-height: 1.4;
    min-height: 42px;
    margin-bottom: 10px;
}

.price {
    color: #e82940;
    font-size: 19px;
    font-weight: bold;
}

.old-price {
    color: #888;
    text-decoration: line-through;
    font-size: 13px;
    margin-top: 5px;
}

.discount {
    display: inline-block;
    background: #fff0d6;
    color: #c35b00;
    padding: 5px 7px;
    border-radius: 5px;
    font-size: 12px;
    margin-top: 8px;
    align-self: flex-start;
}

.deal-button {
    display: block;
    margin-top: auto;
    padding: 11px 5px;
    text-align: center;
    background: #ee3045;
    color: white;
    text-decoration: none;
    font-weight: bold;
    border-radius: 7px;
    margin-top: 12px;
}

.deal-button:hover {
    background: #ca1e33;
}

.empty {
    grid-column: 1 / -1;
    text-align: center;
    padding: 30px;
    background: white;
    border-radius: 10px;
}

.note {
    margin-top: 25px;
    padding: 15px;
    background: #fff8e5;
    border-radius: 8px;
    font-size: 13px;
    line-height: 1.7;
}

footer {
    text-align: center;
    background: #222;
    color: white;
    padding: 24px 12px;
    font-size: 13px;
    line-height: 1.8;
}

@media (max-width: 750px) {
    .products {
        grid-template-columns: repeat(2, minmax(0, 1fr));
        gap: 10px;
    }

    header h1 {
        font-size: 24px;
    }

    .product-info {
        padding: 9px;
    }

    .product h3 {
        font-size: 14px;
    }
}
</style>
</head>

<body>

<header>
    <h1>🔥 SĂN DEAL GIÁ TỐT</h1>
    <p>Chọn deal hay - Mua sắm tiết kiệm mỗi ngày!</p>

    <div class="search-box">
        <input id="searchInput"
               type="search"
               placeholder="Tìm sản phẩm bạn cần...">
        <button onclick="renderProducts()">Tìm</button>
    </div>
</header>

<nav>
    <button onclick="filterCategory('Tất cả')">🏠 Tất cả</button>
    <button onclick="filterCategory('Gia dụng')">🏡 Gia dụng</button>
    <button onclick="filterCategory('Điện tử')">🎧 Điện tử</button>
    <button onclick="filterCategory('Thời trang')">👕 Thời trang</button>
    <button onclick="filterCategory('Làm đẹp')">✨ Làm đẹp</button>
</nav>

<div class="banner">
    <h2>⚡ DEAL HOT MỖI NGÀY ⚡</h2>
    <p>Khám phá sản phẩm hữu ích với mức giá hấp dẫn.</p>
</div>

<main class="container">
    <h2 class="section-title">🔥 Deal nổi bật hôm nay</h2>
    <div class="products" id="productList"></div>

    <div class="note">
        <strong>📢 Lưu ý:</strong>
        Giá và chương trình khuyến mãi có thể thay đổi theo thời gian.
        Vui lòng kiểm tra giá cuối cùng trên trang bán hàng trước khi mua.
        Một số liên kết trên website có thể là liên kết tiếp thị liên kết.
        Website có thể nhận hoa hồng nếu bạn mua hàng qua các liên kết đó,
        mà không làm tăng giá mua của bạn.
    </div>
</main>

<footer>
    <h3>SĂN DEAL GIÁ TỐT</h3>
    <p>Chia sẻ deal hữu ích - Mua sắm thông minh.</p>
    <p>© 2026 SanDealGiaTot</p>
</footer>

<script>
const products = [
    {
        name: "Gậy chụp ảnh điện thoại tripod",
        category: "Điện tử",
        price: 89000,
        oldPrice: 159000,
        image: "https://placehold.co/400x400/ffe8e8/333333?text=Tripod",
        link: "https://shopee.vn/",
        discount: 44
    },
    {
        name: "Đèn LED để bàn học tập",
        category: "Gia dụng",
        price: 79000,
        oldPrice: 129000,
        image: "https://placehold.co/400x400/e8f4ff/333333?text=Den+LED",
        link: "https://shopee.vn/",
        discount: 39
    },
    {
        name: "Tai nghe không dây",
        category: "Điện tử",
        price: 129000,
        oldPrice: 199000,
        image: "https://placehold.co/400x400/e8ffe8/333333?text=Tai+nghe",
        link: "https://shopee.vn/",
        discount: 35
    },
    {
        name: "Túi đeo chéo thời trang",
        category: "Thời trang",
        price: 99000,
        oldPrice: 159000,
        image: "https://placehold.co/400x400/fff2dd/333333?text=Tui+deo",
        link: "https://shopee.vn/",
        discount: 38
    },
    {
        name: "Kệ để đồ đa năng",
        category: "Gia dụng",
        price: 69000,
        oldPrice: 109000,
        image: "https://placehold.co/400x400/f0e8ff/333333?text=Ke+da+nang",
        link: "https://shopee.vn/",
        discount: 37
    },
    {
        name: "Máy massage mini",
        category: "Làm đẹp",
        price: 149000,
        oldPrice: 229000,
        image: "https://placehold.co/400x400/ffe8f5/333333?text=Massage",
        link: "https://shopee.vn/",
        discount: 35
    },
    {
        name: "Bình nước giữ nhiệt",
        category: "Gia dụng",
        price: 85000,
        oldPrice: 139000,
        image: "https://placehold.co/400x400/e8faff/333333?text=Binh+nuoc",
        link: "https://shopee.vn/",
        discount: 39
    },
    {
        name: "Ví mini tiện dụng",
        category: "Thời trang",
        price: 59000,
        oldPrice: 99000,
        image: "https://placehold.co/400x400/fff0e8/333333?text=Vi+mini",
        link: "https://shopee.vn/",
        discount: 40
    }
];

let currentCategory = "Tất cả";

function formatPrice(price) {
    return price.toLocaleString("vi-VN") + "đ";
}

function filterCategory(category) {
    currentCategory = category;
    renderProducts();
}

function renderProducts() {
    const list = document.getElementById("productList");
    const keyword = document.getElementById("searchInput")
        .value.trim().toLowerCase();

    const filtered = products.filter(product => {
        const matchName = product.name.toLowerCase().includes(keyword);
        const matchCategory =
            currentCategory === "Tất cả" ||
            product.category === currentCategory;

        return matchName && matchCategory;
    });

    if (filtered.length === 0) {
        list.innerHTML =
            '<div class="empty">Không tìm thấy sản phẩm phù hợp.</div>';
        return;
    }

    list.innerHTML = filtered.map(product => `
        <article class="product">
            <img src="${product.image}"
                 alt="${product.name}"
                 loading="lazy">

            <div class="product-info">
                <h3>${product.name}</h3>
                <div class="price">${formatPrice(product.price)}</div>
                <div class="old-price">
                    ${formatPrice(product.oldPrice)}
                </div>
                <span class="discount">
                    Giảm ${product.discount}%
                </span>

                <a class="deal-button"
                   href="${product.link}"
                   target="_blank"
                   rel="nofollow sponsored noopener">
                   🛒 SĂN DEAL NGAY
                </a>
            </div>
        </article>
    `).join("");
}

document.getElementById("searchInput")
    .addEventListener("input", renderProducts);

renderProducts();
</script>

</body>
</html>