<template>
  <div class="app-root">
    <header class="site-header">
      <div class="logo">Bolokonondo<span>Records</span></div>
      <nav class="main-nav">
        <a href="#playlists">Playlists</a>
        <a href="#artists">Artistas</a>
        <a href="#about">Nosotros</a>
        <a href="#contact">Contacto</a>
      </nav>
    </header>

    <main>
      <!-- Hero -->
      <section class="hero" id="top">
        <div class="hero-overlay"></div>
        <div class="hero-media">
          <div class="hero-media-gradient"></div>
        </div>
        <div class="hero-content">
          <p class="hero-kicker">Medellín · Independent Label</p>
          <h1 class="hero-title">Bolokonondo<br />Records</h1>
          <p class="hero-tagline">Ritmos urbanos desde Medellín para el mundo.</p>
          <div class="hero-cta-row">
            <a href="#playlists" class="btn btn-primary">Escuchar el sello</a>
            <button class="btn btn-ghost" type="button">
              <span class="play-icon">▶</span>
              Ver teaser
            </button>
          </div>
          <div class="hero-meta">
            <span>· Nuevas voces urbanas</span>
            <span>· Sonido global</span>
            <span>· Energía de barrio</span>
          </div>
        </div>
      </section>

      <!-- Playlists -->
      <section class="section section-playlists" id="playlists">
        <div class="section-header">
          <h2>Playlists destacadas</h2>
          <p>Curadas por el sello para clubs, noches en la ciudad y escuchas profundas.</p>
        </div>
        <div class="cards-grid playlists-grid">
          <article
            v-for="playlist in playlists"
            :key="playlist.id"
            class="card playlist-card"
          >
            <div class="playlist-cover" :class="playlist.coverClass">
              <a
                v-if="playlist.link"
                class="play-button"
                :href="playlist.link"
                target="_blank"
                rel="noreferrer"
                aria-label="Abrir playlist en Spotify"
              >
                ▶
              </a>
              <button
                v-else
                class="play-button"
                type="button"
                aria-label="Vista previa de playlist"
              >
                ▶
              </button>
            </div>
            <div class="card-body">
              <h3>{{ playlist.title }}</h3>
              <p>{{ playlist.description }}</p>
            </div>
          </article>
        </div>

        <!-- Spotify embed for Afrobeat Mundial playlist -->
        <div class="playlist-embed">
          <iframe
            data-testid="embed-iframe"
            style="border-radius: 12px"
            src="https://open.spotify.com/embed/playlist/13lqBKfpObl0xtqWJausLz?utm_source=generator"
            width="100%"
            height="352"
            frameborder="0"
            allowfullscreen
            allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
            loading="lazy"
          ></iframe>
        </div>
      </section>

      <!-- Artists -->
      <section class="section section-artists" id="artists">
        <div class="section-header">
          <h2>Artistas Bolokonondo</h2>
          <p>
            Talento diverso con una misma energía: llevar el sonido urbano más allá de las
            fronteras.
          </p>
        </div>
        <div class="cards-grid artists-grid">
          <article
            v-for="artist in artists"
            :key="artist.id"
            class="card artist-card"
          >
            <div class="artist-photo" :class="artist.photoClass"></div>
            <div class="card-body">
              <h3>{{ artist.name }}</h3>
              <p>{{ artist.description }}</p>
            </div>
          </article>
        </div>
      </section>

      <!-- About -->
      <section class="section section-about" id="about">
        <div class="about-inner">
          <div class="about-text">
            <h2>Sobre Bolokonondo</h2>
            <p>
              Somos un sello independiente enfocado en el género urbano, que piensa desde Medellín
              para el mundo. Amplificamos artistas que transforman su realidad en sonido y
              conectamos las calles de la ciudad con la escena global.
            </p>
          </div>
          <div class="about-tagline">
            <p>Medellín es el punto de partida, nunca el límite.</p>
          </div>
        </div>
      </section>
    </main>

    <!-- Footer -->
    <footer class="site-footer" id="contact">
      <div class="footer-top">
        <div class="footer-brand">
          <div class="logo logo-footer">Bolokonondo<span>Records</span></div>
          <p>Sello urbano independiente con base en Medellín y visión global.</p>
        </div>
        <div class="footer-links">
          <h4>Síguenos</h4>
          <ul>
            <li>
              <a
                :href="links.instagram"
                target="_blank"
                rel="noreferrer"
                aria-label="Instagram Bolokonondo Records"
              >
                Instagram
              </a>
            </li>
            <li>
              <a
                :href="links.spotify"
                target="_blank"
                rel="noreferrer"
                aria-label="Spotify Bolokonondo Records"
              >
                Spotify
              </a>
            </li>
          </ul>
        </div>
        <div class="footer-contact">
          <h4>Contacto</h4>
          <a :href="`mailto:${links.email}`">{{ links.email }}</a>
        </div>
      </div>
      <div class="footer-bottom">
        <p>© <span>{{ currentYear }}</span> Bolokonondo Records. Todos los derechos reservados.</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
const links = {
  instagram: 'https://www.instagram.com/bolokonondo/',
  spotify:
    'https://open.spotify.com/user/31lp4tisnjbgvm7u2oqtk5z3mgci?si=a016996de69a461c',
  email: 'bolokonondorecords@gmail.com',
};

const playlists = [
  {
    id: 'after-hours',
    title: 'Medellín After Hours',
    description: 'Beats densos y atmosféricos para cuando la ciudad no duerme.',
    coverClass: 'cover-1',
    link: '',
  },
  {
    id: 'afrobeat-mundial',
    title: 'Afrobeat Mundial',
    description:
      'Las mejores canciones del Afrobeat del mundo en colaboración con Bolokonondo Records.',
    coverClass: 'cover-2',
    // Official Afrobeat Mundial playlist on Spotify
    link: 'https://open.spotify.com/playlist/13lqBKfpObl0xtqWJausLz',
  },
  {
    id: 'neo-urbano',
    title: 'Neo Urbano Global',
    description:
      'Sonidos híbridos, colaboraciones y futuros himnos que conectan Medellín con el mundo.',
    coverClass: 'cover-3',
    link: '',
  },
];

const artists = [
  {
    id: 'la-nova',
    name: 'La Nova',
    description: 'Voces suaves sobre beats agresivos. Medellín nocturna en cada barra.',
    photoClass: 'artist-1',
  },
  {
    id: 'mono-13',
    name: 'Mono 13',
    description: 'Trap híbrido y melodías oscuras con visión global.',
    photoClass: 'artist-2',
  },
  {
    id: 'ruta-centro',
    name: 'Ruta Centro',
    description:
      'Colectivo de productores que conectan Medellín con escenas de Londres y NYC.',
    photoClass: 'artist-3',
  },
  {
    id: 'knd',
    name: 'KND',
    description: 'Ritmos minimalistas, bajos pesados y letras introspectivas.',
    photoClass: 'artist-4',
  },
];

const currentYear = new Date().getFullYear();
</script>

