<script setup>
import { ref } from 'vue'

const menuOpen = ref(false)
const openFaq = ref(0)

const games = [
  { name: 'Minecraft', detail: 'Java & Bedrock', mark: 'M', tone: 'minecraft', tag: 'NAJPOPULARNIEJSZE' },
  { name: 'Rust', detail: 'Vanilla, modded i więcej', mark: 'R', tone: 'rust', tag: 'NOWOŚĆ' },
  { name: 'Counter-Strike 2', detail: 'Serwery turniejowe', mark: 'CS', tone: 'cs', tag: '' },
  { name: 'ARK: Survival', detail: 'Evolved & Ascended', mark: 'A', tone: 'ark', tag: '' },
  { name: 'Valheim', detail: 'Wikingowie, do dzieła', mark: 'V', tone: 'valheim', tag: '' },
  { name: 'Terraria', detail: 'Przygoda bez końca', mark: 'T', tone: 'terraria', tag: '' },
]

const benefits = [
  { number: '01', title: 'Wydajność bez lagów', text: 'Nowoczesne procesory AMD Ryzen i szybkie dyski NVMe. Twoja rozgrywka zawsze płynna.' },
  { number: '02', title: 'Serwery w Polsce', text: 'Niskie pingi dzięki infrastrukturze w polskim centrum danych. Bliżej = szybciej.' },
  { number: '03', title: 'Pełna kontrola', text: 'Intuicyjny panel, instalacja modów jednym kliknięciem i dostęp do plików serwera.' },
]

const faqs = [
  { question: 'Czy mogę przetestować serwer przed zakupem?', answer: 'Jasne! Każdy nowy serwer możesz przetestować przez 48 godzin. Bez karty i bez zobowiązań.' },
  { question: 'Jak szybko serwer będzie gotowy?', answer: 'Serwer uruchamia się automatycznie zaraz po zamówieniu. Zwykle możesz grać już po kilkudziesięciu sekundach.' },
  { question: 'Czy mogę zmienić plan w dowolnym momencie?', answer: 'Tak. Zwiększ lub zmniejsz zasoby serwera bez utraty świata i konfiguracji. Zmiany wprowadzisz prosto w panelu.' },
]
</script>

<template>
  <div class="site-shell">
    <header class="site-header">
      <a class="brand" href="#" aria-label="Corespawn — strona główna">
        <span class="brand-mark" aria-hidden="true"><span></span><span></span><span></span></span>
        <span>core<span class="brand-light">spawn</span><span class="brand-dot">.</span></span>
      </a>

      <button
        class="menu-toggle"
        type="button"
        :aria-expanded="menuOpen"
        aria-label="Otwórz menu"
        @click="menuOpen = !menuOpen"
      >
        <span></span><span></span>
      </button>

      <nav class="main-nav" :class="{ 'is-open': menuOpen }" aria-label="Nawigacja główna">
        <a href="#gry" @click="menuOpen = false">Gry</a>
        <a href="#dlaczego-my" @click="menuOpen = false">Dlaczego my</a>
        <a href="#cennik" @click="menuOpen = false">Cennik</a>
        <a href="#faq" @click="menuOpen = false">FAQ</a>
        <a class="nav-login" href="#cennik" @click="menuOpen = false">Panel klienta <span aria-hidden="true">↗</span></a>
      </nav>
    </header>

    <main>
      <section class="hero">
        <div class="hero-copy">
          <div class="eyebrow"><span class="live-dot"></span> SERWERY GOTOWE DO GRY</div>
          <h1>Twój świat.<br />Twoje <span>zasady.</span></h1>
          <p class="hero-description">
            Stawiaj serwery gier bez lagów, czekania i zbędnych komplikacji. Ty wybierasz grę — my ogarniamy resztę.
          </p>
          <div class="hero-actions">
            <a class="button button-primary" href="#gry">Wybierz swoją grę <span aria-hidden="true">↗</span></a>
            <a class="button button-quiet" href="#dlaczego-my"><span class="play-icon" aria-hidden="true">▶</span> Poznaj Corespawn</a>
          </div>
          <div class="social-proof">
            <div class="avatar-stack" aria-hidden="true"><span>MK</span><span>JD</span><span>SK</span><span>+</span></div>
            <div><strong>2 400+</strong><span>graczy już z nami</span></div>
            <span class="proof-divider"></span>
            <div class="rating"><span aria-label="5 na 5 gwiazdek">★★★★★</span><small>4.9/5 opinii</small></div>
          </div>
        </div>

        <div class="hero-visual" aria-label="Podgląd panelu zarządzania serwerem">
          <div class="visual-glow"></div>
          <div class="orbit orbit-one"></div>
          <div class="orbit orbit-two"></div>
          <div class="dashboard-card">
            <div class="dashboard-top">
              <div class="window-dots"><i></i><i></i><i></i></div>
              <span class="panel-label">CORESPAWN PANEL</span>
              <span class="panel-menu">•••</span>
            </div>
            <div class="server-heading">
              <div class="server-icon">M</div>
              <div><strong>Survival SMP</strong><small>Minecraft · 1.21.4</small></div>
              <span class="online-pill"><i></i> ONLINE</span>
            </div>
            <div class="server-world">
              <div class="pixel-sun"></div>
              <div class="mountain mountain-back"></div>
              <div class="mountain mountain-front"></div>
              <div class="world-overlay"><span>mc.corespawn.pl</span><button type="button" aria-label="Kopiuj adres serwera">⧉</button></div>
            </div>
            <div class="server-metrics">
              <div><span>GRACZE</span><strong>18 <small>/ 40</small></strong><div class="metric-bar"><i style="width: 45%"></i></div></div>
              <div><span>WYKORZYSTANIE RAM</span><strong>3.2 <small>GB / 8 GB</small></strong><div class="metric-bar"><i style="width: 40%"></i></div></div>
            </div>
            <div class="console-line"><span class="console-caret">›</span> Serwer działa bez zarzutu <span class="console-time">teraz</span></div>
          </div>
          <div class="floating-chip chip-latency"><span class="signal-icon">⌁</span><div><strong>12 ms</strong><small>ping w Polsce</small></div></div>
          <div class="floating-chip chip-uptime"><span class="uptime-icon">↗</span><div><strong>99.9%</strong><small>uptime</small></div></div>
          <div class="visual-caption"><span></span> TWÓJ SERWER. TWOJE ZASADY.</div>
        </div>

        <a class="scroll-cue" href="#gry"><span></span> PRZEWIŃ I ODKRYJ</a>
      </section>

      <section id="gry" class="games-section section-wrap">
        <div class="section-heading">
          <div><div class="eyebrow"><span class="eyebrow-line"></span> TWOJA GRA, TWOJE MIEJSCE</div><h2>Wskakuj do <span>gry.</span></h2></div>
          <a class="text-link" href="#cennik">Zobacz wszystkie gry <span aria-hidden="true">↗</span></a>
        </div>
        <div class="games-grid">
          <a v-for="game in games" :key="game.name" class="game-card" href="#cennik">
            <span v-if="game.tag" class="game-tag">{{ game.tag }}</span>
            <span class="game-mark" :class="`mark-${game.tone}`">{{ game.mark }}</span>
            <span class="game-info"><strong>{{ game.name }}</strong><small>{{ game.detail }}</small></span>
            <span class="game-arrow" aria-hidden="true">↗</span>
          </a>
        </div>
      </section>

      <section id="dlaczego-my" class="why-section section-wrap">
        <div class="why-intro">
          <div class="eyebrow"><span class="eyebrow-line"></span> WIĘCEJ GRY. MNIEJ CZEKAJ.</div>
          <h2>Hosting, który<br /><span>nadąża za Tobą.</span></h2>
          <p>Tworzymy infrastrukturę, której sami chcielibyśmy używać. Bez haczyków. Bez wymówek. Po prostu działa.</p>
          <a class="text-link" href="#cennik">Sprawdź ofertę <span aria-hidden="true">↗</span></a>
        </div>
        <div class="benefit-list">
          <article v-for="benefit in benefits" :key="benefit.number" class="benefit-item">
            <span class="benefit-number">{{ benefit.number }}</span>
            <div><h3>{{ benefit.title }}</h3><p>{{ benefit.text }}</p></div>
            <span class="benefit-check" aria-hidden="true">↗</span>
          </article>
        </div>
      </section>

      <section id="cennik" class="pricing-section section-wrap">
        <div class="pricing-banner">
          <div class="pricing-decoration" aria-hidden="true"><span></span><span></span><span></span></div>
          <div class="pricing-copy">
            <div class="eyebrow"><span class="live-dot"></span> DOBRY MOMENT, ŻEBY ZACZĄĆ</div>
            <h2>Twoja ekipa już<br />na Ciebie <span>czeka.</span></h2>
            <p>Wybierz grę, dobierz plan i postaw serwer w mniej niż minutę.</p>
          </div>
          <div class="pricing-action">
            <div class="price-from"><span>Plany już od</span><strong>9<small>,99 zł</small></strong><span>/ miesiąc</span></div>
            <a class="button button-primary" href="#gry">Znajdź swój serwer <span aria-hidden="true">↗</span></a>
            <small>Bez umowy · Anuluj kiedy chcesz</small>
          </div>
        </div>
      </section>

      <section id="faq" class="faq-section section-wrap">
        <div class="section-heading">
          <div><div class="eyebrow"><span class="eyebrow-line"></span> DOBRZE WIEDZIEĆ</div><h2>Masz pytania?</h2></div>
          <p>Nie ma głupich pytań. Są tylko szybkie odpowiedzi.</p>
        </div>
        <div class="faq-list">
          <article v-for="(faq, index) in faqs" :key="faq.question" class="faq-item" :class="{ 'faq-open': openFaq === index }">
            <button type="button" :aria-expanded="openFaq === index" @click="openFaq = openFaq === index ? -1 : index">
              <span>{{ faq.question }}</span><span class="faq-plus" aria-hidden="true">{{ openFaq === index ? '−' : '+' }}</span>
            </button>
            <p v-if="openFaq === index">{{ faq.answer }}</p>
          </article>
        </div>
      </section>
    </main>

    <footer class="site-footer">
      <div class="footer-main">
        <a class="brand" href="#" aria-label="Corespawn — strona główna">
          <span class="brand-mark" aria-hidden="true"><span></span><span></span><span></span></span>
          <span>core<span class="brand-light">spawn</span><span class="brand-dot">.</span></span>
        </a>
        <p>Twój świat. Twoje zasady.</p>
        <div class="footer-links"><a href="#gry">Gry</a><a href="#cennik">Cennik</a><a href="#faq">Pomoc</a><a href="#dlaczego-my">O nas</a></div>
      </div>
      <div class="footer-bottom"><span>© 2025 Corespawn. Wszystkie prawa zastrzeżone.</span><span><i></i> Wszystkie systemy działają</span><a href="mailto:hello@corespawn.pl">hello@corespawn.pl</a></div>
    </footer>
  </div>
</template>
