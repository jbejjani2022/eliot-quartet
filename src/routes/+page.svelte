<script>
    import '../app.css';
    import { base } from '$app/paths';
    import { Splide, SplideSlide, SplideTrack } from '@splidejs/svelte-splide';
    import '@splidejs/svelte-splide/css';

    let galleryImages = [
      'quartet1.jpg',
      'quartet2.jpg',
      'quartet3.jpg',
      'quartet4.jpg',
      'quartet5.jpg',
      'quartet6.jpg',
      'quartet7.jpg',
      'quartet8.jpg'
    ];

    // Gallery carousel config
    const options = {
      fixedHeight: true,
      type: 'loop',
      drag: true,
      snap: true,
      perPage: 3,
      perMove: 1,
      pauseOnHover: false,
      focus: 0,
      autoplay: true,
      interval: 4000,
      speed: 2000,
      arrows: true,
      padding: '2rem',
      gap: '1.5rem',
      pagination: true,
      width: '100%', // use full container width
      breakpoints: {
        768: {
          perPage: 2,
          gap: '1rem',
          padding: '1rem'
        },
        480: {
          perPage: 1,
          gap: '0.5rem',
          padding: '0.5rem',
          arrows: false // hide arrows on mobile
        }
      }
    }

    // Function to scroll to the About Us section
    function scrollToAbout() {
        const aboutSection = document.getElementById('about-section');
        aboutSection.scrollIntoView({ behavior: 'smooth' });
    }
</script>

<style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    .section {
        width: 100%;
        max-width: 800px;
        padding: 0rem 10%;
        text-align: center;
        margin-bottom: 2rem; /* Ensures consistent spacing */
    }

    /* Style for the down arrow */
    .down-arrow {
        position: absolute;
        bottom: 12%;
        cursor: pointer;
        background-color: rgba(0, 0, 0, 0.3); /* Semi-transparent black */
        border: none;
        padding: 15px; /* Adjust padding */
        border-radius: 50%; /* Make it circular */
        display: flex;
        justify-content: center;
        align-items: center;
        transition: transform 0.3s ease;
    }

    .down-arrow i {
        color: white; /* White arrow */
        font-size: 20px; /* Adjust icon size */
    }

    /* Hover effect */
    .down-arrow:hover {
        transform: scale(1.2);
    }

    /* Hero section adjustments */
    .hero {
        position: relative;
        width: 100vw;
        height: 100vh;
        background: url('/hero-background.jpg') no-repeat center center/cover;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        color: white;
        text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.8);
        margin-bottom: 2rem;
    }

    .text-overlay {
        position: absolute;
        top: 10rem;
    }

    .hero h1 {
      font-size: 3.5rem;
      font-weight: 450;
    }

    /* Splide slide styles */
    :global(.splide__slide) {
      display: flex;
      justify-content: center;
      align-items: center;
    }

    :global(.splide__slide img) {
      width: 100%;
      height: 90%;
      object-fit: cover;
      border-radius: 5px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: transform 0.3s ease;
    }

    :global(.splide__slide:hover img) {
      transform: scale(1.05);
    }

    :global(.splide) {
      max-width: 1200px;
      margin: 0 auto;
      margin-bottom: 3rem;
    }

    .about h2, .contact h2 {
      font-size: 2rem;
      margin-bottom: 1rem;
    }

    .footer {
      background: #222;
      color: white;
      text-align: center;
      padding: 2rem 0;
      width: 100%;
    }

    .social-links {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 1rem;
      margin-bottom: 1rem;
    }

    .social-links a {
      color: white;
      filter: invert(1);
      transition: opacity 0.3s ease;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .email-link {
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .social-links a:hover {
      opacity: 0.8;
    }

    .phone {
      margin-bottom: 1rem;
      font-size: 0.9rem;
    }

    .quartet-name {
      font-size: 1.2rem;
      font-weight: 500;
    }

    @media (max-width: 768px) {
        .hero {
          height: 68vh;
          background-position: center;
          background-size: cover; /* Ensure it fills the container */
        }
        .hero h1 {
          font-size: 3.1rem;
          font-weight: 450;
        }
        .text-overlay {
          top: 9rem;
        }
    }
</style>

<section class="hero">
    <h1 class="text-overlay">The Eliot Quartet</h1>
    <!-- Down arrow in a black/grey box -->
    <button class="down-arrow" aria-label="Scroll to About Us" on:click={scrollToAbout}>
      <i class="fas fa-arrow-down"></i>
  </button>
</section>

<section class="section about" id="about-section">
    <h2>About Us</h2>
    <p>We are a group of Harvard musicians passionate about bringing chamber music to a variety of events and occasions.</p>
    <br>
    <p>Joey Bejjani - Violin</p>
    <p>Renée Perpignan - Violin</p>
    <p>Miller MacDonald - Cello</p>
    <p>Moshi Tang / Masako Yang - Viola</p>
</section>

<section class="section contact">
    <h2>Contact</h2>
    <p>Request us for your event by emailing <a href="mailto:jbejjani@college.harvard.edu">jbejjani@college.harvard.edu</a>.</p>
    <p>Find us on Instagram <a href="https://www.instagram.com/theeliotquartet/" target="_blank" rel="noopener noreferrer" aria-label="Instagram">@theeliotquartet</a>.</p>
</section>

<Splide 
    options={ options } 
    hasTrack={ false } 
    aria-label="Past screening posters"
  >
  <div style="position: relative">
    <SplideTrack>
      {#each galleryImages as img}
        <SplideSlide>
          <img src={img} alt="Eliot Quartet Performance">
        </SplideSlide>
      {/each}
    </SplideTrack>
  </div>

    <div class="splide__progress">
      <div class="splide__progress__bar">
      </div>
    </div>
  </Splide>

<footer class="footer">
    <div class="social-links">
        <a href="https://www.instagram.com/theeliotquartet/" target="_blank" rel="noopener noreferrer" aria-label="Instagram">
            <img src="{base}/instagram.svg" alt="Instagram" width="28" height="28">
        </a>
        <a href="mailto:jbejjani@college.harvard.edu" aria-label="Email" class="email-link">
            <img src="{base}/email.svg" alt="Email" width="40" height="40">
        </a>
    </div>
    <p class="phone">+1 (201) 492-1440</p>
    <p class="quartet-name">The Eliot Quartet</p>
</footer>
