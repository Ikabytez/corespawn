<script setup>
import { ref, watch } from 'vue'

const savedLanguage = localStorage.getItem('corespawn-language')
const language = ref(savedLanguage === 'pl' ? 'pl' : 'en')
const menuOpen = ref(false)
const openFaq = ref(0)

watch(language, (value) => {
  document.documentElement.lang = value
  document.title = value === 'en'
    ? 'Corespawn | Your world. Your rules.'
    : 'Corespawn | Twój świat. Twoje zasady.'
  localStorage.setItem('corespawn-language', value)
}, { immediate: true })

const copy = {
  en: {
    home: 'Corespawn | Your world. Your rules.',
    homeLabel: 'Corespawn | home',
    menuLabel: 'Open menu',
    navLabel: 'Main navigation',
    nav: ['Games', 'Why us', 'Pricing', 'FAQ', 'Client area'],
    languageLabel: 'Select language',
    englishSelected: 'English selected',
    polishSelected: 'Polish selected',
    switchToEnglish: 'Switch language to English',
    switchToPolish: 'Switch language to Polish',
    heroEyebrow: 'SERVERS READY TO PLAY',
    heroTitle: ['Your world.', 'Your', 'rules.'],
    heroDescription: 'Launch game servers without lag, waiting, or hassle. You pick the game | we take care of the rest.',
    chooseGame: 'Choose your game',
    discover: 'Discover Corespawn',
    playerCount: 'players already here',
    ratingLabel: '5 out of 5 stars',
    reviews: '4.9/5 reviews',
    dashboardLabel: 'Server management panel preview',
    copyServer: 'Copy server address',
    players: 'PLAYERS',
    memory: 'MEMORY USAGE',
    serverHealthy: 'Server running smoothly',
    ping: 'ping in Poland',
    uptime: 'uptime',
    visualCaption: 'YOUR SERVER. YOUR RULES.',
    scrollCue: 'SCROLL TO DISCOVER',
    gamesEyebrow: 'YOUR GAME, YOUR PLACE',
    gamesTitle: ['Jump into', 'the game.'],
    allGames: 'Explore all games',
    games: [
      { name: 'Minecraft', detail: 'Java & Bedrock', mark: 'M', tone: 'minecraft', tag: 'MOST POPULAR' },
      { name: 'Rust', detail: 'Vanilla, modded & more', mark: 'R', tone: 'rust', tag: 'NEW' },
      { name: 'Counter-Strike 2', detail: 'Tournament-ready servers', mark: 'CS', tone: 'cs', tag: '' },
      { name: 'ARK: Survival', detail: 'Evolved & Ascended', mark: 'A', tone: 'ark', tag: '' },
      { name: 'Valheim', detail: 'Vikings, get ready', mark: 'V', tone: 'valheim', tag: '' },
      { name: 'Terraria', detail: 'An endless adventure', mark: 'T', tone: 'terraria', tag: '' },
    ],
    whyEyebrow: 'MORE PLAY. LESS WAIT.',
    whyTitle: ['Hosting that', 'keeps up with you.'],
    whyDescription: 'We build the infrastructure we wish we had. No catches. No excuses. It just works.',
    offer: 'Explore our plans',
    benefits: [
      { number: '01', title: 'Lag-free performance', text: 'Powered by modern AMD Ryzen processors and fast NVMe drives. Keep your gameplay smooth.' },
      { number: '02', title: 'Servers in Poland', text: 'Low ping, thanks to infrastructure in a Polish data centre. Closer means faster.' },
      { number: '03', title: 'You’re in control', text: 'An intuitive control panel, one-click mod installs, and full access to your server files.' },
    ],
    pricingEyebrow: 'A GREAT TIME TO GET STARTED',
    pricingTitle: ['Your crew is', 'waiting for', 'you.'],
    pricingDescription: 'Pick a game, choose a plan, and launch your server in under a minute.',
    plansFrom: 'Plans from',
    month: '/ month',
    findServer: 'Find your server',
    noContract: 'No contracts · Cancel anytime',
    faqEyebrow: 'GOOD TO KNOW',
    faqTitle: 'Questions?',
    faqDescription: 'No silly questions. Just quick answers.',
    faqs: [
      { question: 'Can I try a server before buying?', answer: 'Absolutely! Try every new server for 48 hours. No card details and no commitment.' },
      { question: 'How quickly will my server be ready?', answer: 'Your server is provisioned automatically after checkout. You can usually start playing within seconds.' },
      { question: 'Can I change my plan at any time?', answer: 'Yes. Upgrade or downgrade your server resources without losing your world or settings. Make changes right from the control panel.' },
    ],
    footerTagline: 'Your world. Your rules.',
    footerLinks: ['Games', 'Pricing', 'Support', 'About us'],
    copyright: '© 2025 Corespawn. All rights reserved.',
    systemStatus: 'All systems operational',
    emailLabel: 'Email Corespawn',
  },
  pl: {
    home: 'Corespawn | Twój świat. Twoje zasady.',
    homeLabel: 'Corespawn | strona główna',
    menuLabel: 'Otwórz menu',
    navLabel: 'Nawigacja główna',
    nav: ['Gry', 'Dlaczego my', 'Cennik', 'FAQ', 'Panel klienta'],
    languageLabel: 'Wybierz język',
    englishSelected: 'Wybrano język angielski',
    polishSelected: 'Wybrano język polski',
    switchToEnglish: 'Przełącz język na angielski',
    switchToPolish: 'Przełącz język na polski',
    heroEyebrow: 'SERWERY GOTOWE DO GRY',
    heroTitle: ['Twój świat.', 'Twoje', 'zasady.'],
    heroDescription: 'Stawiaj serwery gier bez lagów, czekania i zbędnych komplikacji. Ty wybierasz grę | my ogarniamy resztę.',
    chooseGame: 'Wybierz swoją grę',
    discover: 'Poznaj Corespawn',
    playerCount: 'graczy już z nami',
    ratingLabel: '5 na 5 gwiazdek',
    reviews: '4.9/5 opinii',
    dashboardLabel: 'Podgląd panelu zarządzania serwerem',
    copyServer: 'Kopiuj adres serwera',
    players: 'GRACZE',
    memory: 'WYKORZYSTANIE RAM',
    serverHealthy: 'Serwer działa bez zarzutu',
    ping: 'ping w Polsce',
    uptime: 'dostępność',
    visualCaption: 'TWÓJ SERWER. TWOJE ZASADY.',
    scrollCue: 'PRZEWIŃ I ODKRYJ',
    gamesEyebrow: 'TWOJA GRA, TWOJE MIEJSCE',
    gamesTitle: ['Wskakuj do', 'gry.'],
    allGames: 'Zobacz wszystkie gry',
    games: [
      { name: 'Minecraft', detail: 'Java & Bedrock', mark: 'M', tone: 'minecraft', tag: 'NAJPOPULARNIEJSZE' },
      { name: 'Rust', detail: 'Vanilla, modded i więcej', mark: 'R', tone: 'rust', tag: 'NOWOŚĆ' },
      { name: 'Counter-Strike 2', detail: 'Serwery turniejowe', mark: 'CS', tone: 'cs', tag: '' },
      { name: 'ARK: Survival', detail: 'Evolved & Ascended', mark: 'A', tone: 'ark', tag: '' },
      { name: 'Valheim', detail: 'Wikingowie, do dzieła', mark: 'V', tone: 'valheim', tag: '' },
      { name: 'Terraria', detail: 'Przygoda bez końca', mark: 'T', tone: 'terraria', tag: '' },
    ],
    whyEyebrow: 'WIĘCEJ GRY. MNIEJ CZEKAJ.',
    whyTitle: ['Hosting, który', 'nadąża za Tobą.'],
    whyDescription: 'Tworzymy infrastrukturę, której sami chcielibyśmy używać. Bez haczyków. Bez wymówek. Po prostu działa.',
    offer: 'Sprawdź ofertę',
    benefits: [
      { number: '01', title: 'Wydajność bez lagów', text: 'Nowoczesne procesory AMD Ryzen i szybkie dyski NVMe. Twoja rozgrywka zawsze płynna.' },
      { number: '02', title: 'Serwery w Polsce', text: 'Niskie pingi dzięki infrastrukturze w polskim centrum danych. Bliżej = szybciej.' },
      { number: '03', title: 'Pełna kontrola', text: 'Intuicyjny panel, instalacja modów jednym kliknięciem i dostęp do plików serwera.' },
    ],
    pricingEyebrow: 'DOBRY MOMENT, ŻEBY ZACZĄĆ',
    pricingTitle: ['Twoja ekipa już', 'na Ciebie', 'czeka.'],
    pricingDescription: 'Wybierz grę, dobierz plan i postaw serwer w mniej niż minutę.',
    plansFrom: 'Plany już od',
    month: '/ miesiąc',
    findServer: 'Znajdź swój serwer',
    noContract: 'Bez umowy · Anuluj kiedy chcesz',
    faqEyebrow: 'DOBRZE WIEDZIEĆ',
    faqTitle: 'Masz pytania?',
    faqDescription: 'Nie ma głupich pytań. Są tylko szybkie odpowiedzi.',
    faqs: [
      { question: 'Czy mogę przetestować serwer przed zakupem?', answer: 'Jasne! Każdy nowy serwer możesz przetestować przez 48 godzin. Bez karty i bez zobowiązań.' },
      { question: 'Jak szybko serwer będzie gotowy?', answer: 'Serwer uruchamia się automatycznie zaraz po zamówieniu. Zwykle możesz grać już po kilkudziesięciu sekundach.' },
      { question: 'Czy mogę zmienić plan w dowolnym momencie?', answer: 'Tak. Zwiększ lub zmniejsz zasoby serwera bez utraty świata i konfiguracji. Zmiany wprowadzisz prosto w panelu.' },
    ],
    footerTagline: 'Twój świat. Twoje zasady.',
    footerLinks: ['Gry', 'Cennik', 'Pomoc', 'O nas'],
    copyright: '© 2025 Corespawn. Wszystkie prawa zastrzeżone.',
    systemStatus: 'Wszystkie systemy działają',
    emailLabel: 'Napisz do Corespawn',
  },
}

const t = () => copy[language.value]
</script>

<template>
  <div class="site-shell">
    <header class="site-header">
      <a class="brand" href="#" :aria-label="t().homeLabel">
        <span class="brand-mark" aria-hidden="true"><span></span><span></span><span></span></span>
        <span>core<span class="brand-light">spawn</span><span class="brand-dot">.</span></span>
      </a>

      <div class="language-toggle" role="group" :aria-label="t().languageLabel">
        <button
          class="language-option"
          :class="{ 'language-active': language === 'en' }"
          type="button"
          :aria-label="language === 'en' ? t().englishSelected : t().switchToEnglish"
          :aria-pressed="language === 'en'"
          @click="language = 'en'"
        >EN</button>
        <span class="language-divider" aria-hidden="true">|</span>
        <button
          class="language-option"
          :class="{ 'language-active': language === 'pl' }"
          type="button"
          :aria-label="language === 'pl' ? t().polishSelected : t().switchToPolish"
          :aria-pressed="language === 'pl'"
          @click="language = 'pl'"
        >PL</button>
      </div>

      <button
        class="menu-toggle"
        type="button"
        :aria-expanded="menuOpen"
        :aria-label="t().menuLabel"
        @click="menuOpen = !menuOpen"
      >
        <span></span><span></span>
      </button>

      <nav class="main-nav" :class="{ 'is-open': menuOpen }" :aria-label="t().navLabel">
        <a href="#gry" @click="menuOpen = false">{{ t().nav[0] }}</a>
        <a href="#dlaczego-my" @click="menuOpen = false">{{ t().nav[1] }}</a>
        <a href="#cennik" @click="menuOpen = false">{{ t().nav[2] }}</a>
        <a href="#faq" @click="menuOpen = false">{{ t().nav[3] }}</a>
        <a class="nav-login" href="#cennik" @click="menuOpen = false">{{ t().nav[4] }} <span aria-hidden="true">↗</span></a>
      </nav>
    </header>

    <main>
      <section class="hero">
        <div class="hero-copy">
          <div class="eyebrow"><span class="live-dot"></span> {{ t().heroEyebrow }}</div>
          <h1>{{ t().heroTitle[0] }}<br />{{ t().heroTitle[1] }} <span>{{ t().heroTitle[2] }}</span></h1>
          <p class="hero-description">{{ t().heroDescription }}</p>
          <div class="hero-actions">
            <a class="button button-primary" href="#gry">{{ t().chooseGame }} <span aria-hidden="true">↗</span></a>
            <a class="button button-quiet" href="#dlaczego-my"><span class="play-icon" aria-hidden="true">▶</span> {{ t().discover }}</a>
          </div>
          <div class="social-proof">
            <div class="avatar-stack" aria-hidden="true"><span>MK</span><span>JD</span><span>SK</span><span>+</span></div>
            <div><strong>2,400+</strong><span>{{ t().playerCount }}</span></div>
            <span class="proof-divider"></span>
            <div class="rating"><span :aria-label="t().ratingLabel">★★★★★</span><small>{{ t().reviews }}</small></div>
          </div>
        </div>

        <div class="hero-visual" :aria-label="t().dashboardLabel">
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
              <div class="world-overlay"><span>mc.corespawn.pl</span><button type="button" :aria-label="t().copyServer">⧉</button></div>
            </div>
            <div class="server-metrics">
              <div><span>{{ t().players }}</span><strong>18 <small>/ 40</small></strong><div class="metric-bar"><i style="width: 45%"></i></div></div>
              <div><span>{{ t().memory }}</span><strong>3.2 <small>GB / 8 GB</small></strong><div class="metric-bar"><i style="width: 40%"></i></div></div>
            </div>
            <div class="console-line"><span class="console-caret">›</span> {{ t().serverHealthy }} <span class="console-time">{{ language === 'en' ? 'now' : 'teraz' }}</span></div>
          </div>
          <div class="floating-chip chip-latency"><span class="signal-icon">⌁</span><div><strong>12 ms</strong><small>{{ t().ping }}</small></div></div>
          <div class="floating-chip chip-uptime"><span class="uptime-icon">↗</span><div><strong>99.9%</strong><small>{{ t().uptime }}</small></div></div>
          <div class="visual-caption"><span></span> {{ t().visualCaption }}</div>
        </div>

        <a class="scroll-cue" href="#gry"><span></span> {{ t().scrollCue }}</a>
      </section>

      <section id="gry" class="games-section section-wrap">
        <div class="section-heading">
          <div><div class="eyebrow"><span class="eyebrow-line"></span> {{ t().gamesEyebrow }}</div><h2>{{ t().gamesTitle[0] }} <span>{{ t().gamesTitle[1] }}</span></h2></div>
          <a class="text-link" href="#cennik">{{ t().allGames }} <span aria-hidden="true">↗</span></a>
        </div>
        <div class="games-grid">
          <a v-for="game in t().games" :key="game.name" class="game-card" href="#cennik">
            <span v-if="game.tag" class="game-tag">{{ game.tag }}</span>
            <span class="game-mark" :class="`mark-${game.tone}`">{{ game.mark }}</span>
            <span class="game-info"><strong>{{ game.name }}</strong><small>{{ game.detail }}</small></span>
            <span class="game-arrow" aria-hidden="true">↗</span>
          </a>
        </div>
      </section>

      <section id="dlaczego-my" class="why-section section-wrap">
        <div class="why-intro">
          <div class="eyebrow"><span class="eyebrow-line"></span> {{ t().whyEyebrow }}</div>
          <h2>{{ t().whyTitle[0] }}<br /><span>{{ t().whyTitle[1] }}</span></h2>
          <p>{{ t().whyDescription }}</p>
          <a class="text-link" href="#cennik">{{ t().offer }} <span aria-hidden="true">↗</span></a>
        </div>
        <div class="benefit-list">
          <article v-for="benefit in t().benefits" :key="benefit.number" class="benefit-item">
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
            <div class="eyebrow"><span class="live-dot"></span> {{ t().pricingEyebrow }}</div>
            <h2>{{ t().pricingTitle[0] }}<br />{{ t().pricingTitle[1] }} <span>{{ t().pricingTitle[2] }}</span></h2>
            <p>{{ t().pricingDescription }}</p>
          </div>
          <div class="pricing-action">
            <div class="price-from"><span>{{ t().plansFrom }}</span><strong>9<small>{{ language === 'en' ? '.99 PLN' : ',99 zł' }}</small></strong><span>{{ t().month }}</span></div>
            <a class="button button-primary" href="#gry">{{ t().findServer }} <span aria-hidden="true">↗</span></a>
            <small>{{ t().noContract }}</small>
          </div>
        </div>
      </section>

      <section id="faq" class="faq-section section-wrap">
        <div class="section-heading">
          <div><div class="eyebrow"><span class="eyebrow-line"></span> {{ t().faqEyebrow }}</div><h2>{{ t().faqTitle }}</h2></div>
          <p>{{ t().faqDescription }}</p>
        </div>
        <div class="faq-list">
          <article v-for="(faq, index) in t().faqs" :key="faq.question" class="faq-item" :class="{ 'faq-open': openFaq === index }">
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
        <a class="brand" href="#" :aria-label="t().homeLabel">
          <span class="brand-mark" aria-hidden="true"><span></span><span></span><span></span></span>
          <span>core<span class="brand-light">spawn</span><span class="brand-dot">.</span></span>
        </a>
        <p>{{ t().footerTagline }}</p>
        <div class="footer-links">
          <a href="#gry">{{ t().footerLinks[0] }}</a><a href="#cennik">{{ t().footerLinks[1] }}</a><a href="#faq">{{ t().footerLinks[2] }}</a><a href="#dlaczego-my">{{ t().footerLinks[3] }}</a>
        </div>
      </div>
      <div class="footer-bottom"><span>{{ t().copyright }}</span><span><i></i> {{ t().systemStatus }}</span><a href="mailto:hello@corespawn.pl" :aria-label="t().emailLabel">hello@corespawn.pl</a></div>
    </footer>
  </div>
</template>
