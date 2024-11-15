<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>검색 바 기능</title>

    <style>
      .searchbar {
        width: 300px;
        margin: 0 auto;
      }
      .search-input {
        width: 100%;
        padding: 10px;
        font-size: 16px;
        margin-bottom: 20px;
        box-sizing: border-box;
      }
      .card-wrap {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
      }
      .card {
        width: 200px;
        border: 1px solid #ccc;
        padding: 20px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
      }
      .card-title {
        font-size: 18px;
        font-weight: bold;
        margin-bottom: 10px;
      }
      .card-content {
        font-size: 14px;
      }
    </style>

  </head>
  <body>
    <!-- 검색바 -->
    <div class="searchbar">
      <input
        type="text"
        placeholder="카드 제목을 검색하세요..."
        class="search-input"
      />
    </div>

    <!-- 카드 목록 -->
    <div class="card-wrap">
      <!-- 데이터 연동 -->
    </div>

    <!-- js -->
    <script>
      // json 데이터를 불러온다고 가정
      //  fetch("data/card.json")
      //   .then((response) => response.json())
      //   .then((data) => {
      //    cards = data;
      //    renderCards(cards);
      //   })
      //   .catch((err) => console.log(err));

      const cards = [
        { title: "사과", content: "이것은 사과입니다." },
        { title: "바나나", content: "이것은 바나나입니다." },
        { title: "포도", content: "이것은 포도입니다." },
        { title: "체리", content: "이것은 체리입니다." },
        { title: "오렌지", content: "이것은 오렌지입니다." },
        { title: "Apple", content: "This is an apple" },
        { title: "Banana", content: "This is a banana" },
        { title: "Grape", content: "This is a grape" },
        { title: "CHERRY", content: "This is a cherry" },
        { title: "Orange", content: "This is a orange" },
      ];

      const cardWrap = document.querySelector(".card-wrap");
      const searchInput = document.querySelector(".search-input");

      // 카드 데이터를 화면에 출력하는 함수
      const renderCards = (cards) => {
        cardWrap.innerHTML = ""; // 이전 카드들을 제거
        cards.forEach((card) => {
          const cardElement = document.createElement("div");
          cardElement.className = "card";
          cardElement.innerHTML = `
      <div class="card-title">${card.title}</div>
      <div class="card-content">${card.content}</div>`;
          cardWrap.appendChild(cardElement);
        });
      };

      // 처음에 모든 카드를 표시
      renderCards(cards);

      // 검색어에 따라 카드를 필터링하는 기능
      searchInput.addEventListener("input", (e) => {
        // console.log(e.target.value);
        const filter = e.target.value.toLowerCase();
        const filteredCards = cards.filter((card) => {
          return card.title.toLowerCase().includes(filter);
        });
        renderCards(filteredCards);
      });
    </script>

  </body>
</html>
