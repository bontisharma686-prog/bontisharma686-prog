<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Anime Vault Showcase</title>
  <style>
    /* Reset & Base Styles */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background-color: #0b0c10;
      color: #c5c6c7;
      padding: 20px;
    }

    .container {
      max-width: 1100px;
      margin: 0 auto;
    }

    /* Hero Header */
    header {
      text-align: center;
      padding: 40px 20px;
      background: linear-gradient(135deg, #1f2833 0%, #0b0c10 100%);
      border: 1px solid #45a29e;
      border-radius: 12px;
      margin-bottom: 30px;
      box-shadow: 0 0 15px rgba(102, 252, 241, 0.2);
    }

    header h1 {
      font-size: 2.8rem;
      color: #66fcf1;
      margin-bottom: 10px;
      text-transform: uppercase;
      letter-spacing: 2px;
    }

    header p {
      color: #c5c6c7;
      font-size: 1.1rem;
    }

    /* Stats Bar */
    .stats-bar {
      display: flex;
      justify-content: center;
      gap: 30px;
      margin-top: 20px;
    }

    .stat-box {
      background: #1f2833;
      padding: 10px 20px;
      border-radius: 8px;
      border: 1px solid #45a29e;
      text-align: center;
    }

    .stat-box span {
      display: block;
      font-size: 1.4rem;
      font-weight: bold;
      color: #66fcf1;
    }

    /* Controls: Search & Genre Filter */
    .controls {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 30px;
    }

    .search-box input {
      padding: 10px 15px;
      width: 280px;
      border-radius: 6px;
      border: 1px solid #45a29e;
      background-color: #1f2833;
      color: #fff;
      outline: none;
    }

    .filter-buttons {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
    }

    .btn {
      padding: 8px 16px;
      background-color: #1f2833;
      color: #66fcf1;
      border: 1px solid #45a29e;
      border-radius: 6px;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    .btn:hover, .btn.active {
      background-color: #45a29e;
      color: #0b0c10;
      font-weight: bold;
    }

    /* Grid Layout */
    .section-title {
      font-size: 1.8rem;
      color: #66fcf1;
      margin-bottom: 20px;
      border-bottom: 2px solid #45a29e;
      display: inline-block;
      padding-bottom: 5px;
    }

    .anime-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 25px;
      margin-bottom: 50px;
    }

    .anime-card {
      background-color: #1f2833;
      border-radius: 10px;
      overflow: hidden;
      border: 1px solid #2d3748;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      display: flex;
      flex-direction: column;
    }

    .anime-card:hover {
      transform: translateY(-6px);
      box-shadow: 0 10px 20px rgba(102, 252, 241, 0.25);
    }

    .card-img-container {
      position: relative;
      height: 320px;
    }

    .card-img-container img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .badge {
      position: absolute;
      top: 10px;
      left: 10px;
      background: rgba(11, 12, 16, 0.85);
      color: #66fcf1;
      padding: 4px 10px;
      border-radius: 4px;
      font-size: 0.8rem;
      border: 1px solid #45a29e;
    }

    .rating {
      position: absolute;
      bottom: 10px;
      right: 10px;
      background: rgba(11, 12, 16, 0.85);
      color: #ffd700;
      padding: 4px 8px;
      border-radius: 4px;
      font-weight: bold;
    }

    .anime-content {
      padding: 15px;
      display: flex;
      flex-direction: column;
      flex-grow: 1;
    }

    .anime-title {
      font-size: 1.3rem;
      color: #fff;
      margin-bottom: 8px;
    }

    .anime-desc {
      font-size: 0.9rem;
      color: #c5c6c7;
      margin-bottom: 15px;
      line-height: 1.4;
      flex-grow: 1;
    }

    .card-btn {
      width: 100%;
      padding: 10px;
      background-color: #45a29e;
      color: #0b0c10;
      border: none;
      border-radius: 6px;
      font-weight: bold;
      cursor: pointer;
      transition: background 0.3s ease;
    }

    .card-btn:hover {
      background-color: #66fcf1;
    }

    /* Modal Popup */
    .modal-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.85);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      padding: 20px;
    }

    .modal-content {
      background: #1f2833;
      border: 1px solid #66fcf1;
      border-radius: 12px;
      max-width: 700px;
      width: 100%;
      padding: 25px;
      position: relative;
      box-shadow: 0 0 25px rgba(102, 252, 241, 0.3);
    }

    .close-modal {
      position: absolute;
      top: 15px;
      right: 20px;
      font-size: 1.8rem;
      color: #66fcf1;
      cursor: pointer;
    }

    .modal-title {
      color: #fff;
      font-size: 1.8rem;
      margin-bottom: 10px;
    }

    .video-container {
      position: relative;
      padding-bottom: 56.25%; /* 16:9 Aspect Ratio */
      height: 0;
      overflow: hidden;
      margin-top: 15px;
      border-radius: 8px;
    }

    .video-container iframe {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      border: 0;
    }

    /* Quote Generator Section */
    .quote-section {
      background: #1f2833;
      border: 1px solid #45a29e;
      border-radius: 10px;
      padding: 25px;
      text-align: center;
      margin-bottom: 50px;
    }

    .quote-text {
      font-size: 1.2rem;
      font-style: italic;
      color: #fff;
      margin-bottom: 10px;
    }

    .quote-author {
      color: #66fcf1;
      font-weight: bold;
      margin-bottom: 20px;
    }

    /* Tier List Section */
    .tier-section {
      margin-bottom: 50px;
    }

    .tier-row {
      display: flex;
      background-color: #1f2833;
      border: 1px solid #2d3748;
      margin-bottom: 10px;
      border-radius: 8px;
      overflow: hidden;
      min-height: 80px;
    }

    .tier-label {
      width: 80px;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 1.5rem;
      font-weight: bold;
      color: #0b0c10;
    }

    .tier-s { background-color: #ff7f7f; }
    .tier-a { background-color: #ffbf7f; }
    .tier-b { background-color: #ffdf7f; }

    .tier-items {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      padding: 10px;
      align-items: center;
      flex-grow: 1;
    }

    .tier-chip {
      background-color: #0b0c10;
      color: #66fcf1;
      border: 1px solid #45a29e;
      padding: 8px 14px;
      border-radius: 20px;
      font-size: 0.9rem;
    }

    footer {
      text-align: center;
      padding: 20px;
      color: #c5c6c7;
      font-size: 0.85rem;
      border-top: 1px solid #1f2833;
    }
  </style>
</head>
<body>

  <div class="container">
    <!-- Header -->
    <header>
      <h1>⚡ Anime Vault</h1>
      <p>Your portal for exploring legendary series, trailers, quotes, and ratings.</p>
      <div class="stats-bar">
        <div class="stat-box">
          <span id="total-count">3</span>
          Vault Series
        </div>
        <div class="stat-box">
          <span>9.2</span>
          Avg Rating
        </div>
      </div>
    </header>

    <!-- Controls -->
    <div class="controls">
      <div class="search-box">
        <input type="text" id="searchInput" placeholder="Search anime title..." onkeyup="filterAnime()">
      </div>
      <div class="filter-buttons">
        <button class="btn active" onclick="filterGenre('All', this)">All</button>
        <button class="btn" onclick="filterGenre('Sci-Fi', this)">Sci-Fi</button>
        <button class="btn" onclick="filterGenre('Action', this)">Action</button>
        <button class="btn" onclick="filterGenre('Fantasy', this)">Fantasy</button>
      </div>
    </div>

    <!-- Showcase Section -->
    <h2 class="section-title">Featured Vault Showcase</h2>
    <div class="anime-grid" id="animeGrid">
      
      <!-- Anime Card 1 -->
      <div class="anime-card" data-genre="Sci-Fi" data-title="cyberpunk edgerunners">
        <div class="card-img-container">
          <span class="badge">Sci-Fi</span>
          <span class="rating">★ 9.3</span>
          <img src="https://images.unsplash.com/photo-1578632767115-351597cf2477?w=500" alt="Cyberpunk Edgerunners">
        </div>
        <div class="anime-content">
          <h3 class="anime-title">Cyberpunk: Edgerunners</h3>
          <p class="anime-desc">A street kid trying to survive in a technology and body modification-obsessed city of the future.</p>
          <button class="card-btn" onclick="openModal('Cyberpunk: Edgerunners', 'A street kid trying to survive in a technology and body modification-obsessed city of the future. Lost everything, he chooses to stay alive by becoming an edgerunner—a mercenary outlaw.', 'https://www.youtube.com/embed/JtqIas3bYhg')">View Details & Trailer</button>
        </div>
      </div>

      <!-- Anime Card 2 -->
      <div class="anime-card" data-genre="Action" data-title="demon slayer kimetsu no yaiba">
        <div class="card-img-container">
          <span class="badge">Action</span>
          <span class="rating">★ 9.1</span>
          <img src="https://images.unsplash.com/photo-1534447677768-be436bb09401?w=500" alt="Demon Slayer">
        </div>
        <div class="anime-content">
          <h3 class="anime-title">Demon Slayer</h3>
          <p class="anime-desc">A young man embarks on a quest to slay demons and cure his demonized sister.</p>
          <button class="card-btn" onclick="openModal('Demon Slayer: Kimetsu no Yaiba', 'Tanjiro Kamado sets off on a quest to become a Demon Slayer after his family is slaughtered and his younger sister Nezuko turned into a demon.', 'https://www.youtube.com/embed/VQGCBt6b51g')">View Details & Trailer</button>
        </div>
      </div>

      <!-- Anime Card 3 -->
      <div class="anime-card" data-genre="Fantasy" data-title="frieren beyond journey's end">
        <div class="card-img-container">
          <span class="badge">Fantasy</span>
          <span class="rating">★ 9.5</span>
          <img src="https://images.unsplash.com/photo-1563089145-599997674d42?w=500" alt="Frieren">
        </div>
        <div class="anime-content">
          <h3 class="anime-title">Frieren: Beyond Journey's End</h3>
          <p class="anime-desc">An elven mage reflects on human life and mortality after her hero party disbands.</p>
          <button class="card-btn" onclick="openModal('Frieren: Beyond Journey\'s End', 'An elf mage and her courageous fellow adventurers have defeated the Demon King and brought peace to the land. But Frieren must navigate time and loss as an immortal being.', 'https://www.youtube.com/embed/qgQunD1kbf0')">View Details & Trailer</button>
        </div>
      </div>

    </div>

    <!-- Quote Generator -->
    <div class="quote-section">
      <h2 class="section-title" style="border: none; margin-bottom: 10px;">🔥 Iconic Wisdom</h2>
      <p class="quote-text" id="quoteText">"Push through the pain, giving up hurts more."</p>
      <div class="quote-author" id="quoteAuthor">— Vegeta (Dragon Ball Z)</div>
      <button class="btn active" onclick="getRandomQuote()">Get Random Quote</button>
    </div>

    <!-- Tier List Section -->
    <div class="tier-section">
      <h2 class="section-title">🏆 Anime Rating Tier List</h2>
      <div class="tier-row">
        <div class="tier-label tier-s">S</div>
        <div class="tier-items">
          <div class="tier-chip">Cyberpunk: Edgerunners</div>
          <div class="tier-chip">Frieren: Beyond Journey's End</div>
        </div>
      </div>
      <div class="tier-row">
        <div class="tier-label tier-a">A</div>
        <div class="tier-items">
          <div class="tier-chip">Demon Slayer</div>
        </div>
      </div>
      <div class="tier-row">
        <div class="tier-label tier-b">B</div>
        <div class="tier-items">
          <div class="tier-chip">Your Favorite Show Here</div>
        </div>
      </div>
    </div>

    <footer>
      <p>© 2026 Anime Vault • Personal Custom Fan Page</p>
    </footer>
  </div>

  <!-- Modal Window -->
  <div class="modal-overlay" id="modalOverlay">
    <div class="modal-content">
      <span class="close-modal" onclick="closeModal()">&times;</span>
      <h2 class="modal-title" id="modalTitle">Anime Title</h2>
      <p id="modalDesc" style="line-height: 1.5; margin-bottom: 15px;"></p>
      <div class="video-container">
        <iframe id="modalIframe" src="" allowfullscreen></iframe>
      </div>
    </div>
  </div>

  <!-- JavaScript Functionality -->
  <script>
    // Quotes Database
    const quotes = [
      { text: '"Push through the pain, giving up hurts more."', author: '— Vegeta (Dragon Ball Z)' },
      { text: '"Fear is not evil. It tells you what your weakness is."', author: '— Gildarts Clive (Fairy Tail)' },
      { text: '"If you don\'t take risks, you can\'t create a future."', author: '— Monkey D. Luffy (One Piece)' },
      { text: '"It\'s not the face that makes someone a monster, it\'s the choices they make with their lives."', author: '— Naruto Uzumaki (Naruto)' }
    ];

    // Get Random Quote
    function getRandomQuote() {
      const randomIndex = Math.floor(Math.random() * quotes.length);
      document.getElementById('quoteText').innerText = quotes[randomIndex].text;
      document.getElementById('quoteAuthor').innerText = quotes[randomIndex].author;
    }

    // Modal Control
    function openModal(title, desc, trailerUrl) {
      document.getElementById('modalTitle').innerText = title;
      document.getElementById('modalDesc').innerText = desc;
      document.getElementById('modalIframe').src = trailerUrl;
      document.getElementById('modalOverlay').style.display = 'flex';
    }

    function closeModal() {
      document.getElementById('modalOverlay').style.display = 'none';
      document.getElementById('modalIframe').src = ''; // Stop video
    }

    // Filter by Genre
    function filterGenre(genre, element) {
      const cards = document.querySelectorAll('.anime-card');
      const buttons = document.querySelectorAll('.filter-buttons .btn');
      
      buttons.forEach(btn => btn.classList.remove('active'));
      element.classList.add('active');

      cards.forEach(card => {
        if (genre === 'All' || card.getAttribute('data-genre') === genre) {
          card.style.display = 'flex';
        } else {
          card.style.display = 'none';
        }
      });
    }

    // Search Filter
    function filterAnime() {
      const input = document.getElementById('searchInput').value.toLowerCase();
      const cards = document.querySelectorAll('.anime-card');

      cards.forEach(card => {
        const title = card.getAttribute('data-title');
        if (title.includes(input)) {
          card.style.display = 'flex';
        } else {
          card.style.display = 'none';
        }
      });
    }
  </script>
</body>
</html>
