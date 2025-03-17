<script>
    import '../app.css';

    let galleryImages = [
      'quartet1.jpg',
      'quartet2.jpg',
      'quartet4.jpg',
    ];
</script>

<style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    .section, .gallery-container {
        width: 100%;
        max-width: 800px;
        padding: 0rem 10%;
        text-align: center;
        margin-bottom: 2rem; /* Ensures consistent spacing */
    }

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
        margin-bottom: 2rem; /* Ensures the same spacing below the hero */
    }

    .gallery-container {
        display: flex;
        justify-content: center;
        gap: 1rem;
        width: 100%;
        max-width: 800px;
    }

    .hero h1 {
      font-size: 4rem;
      font-weight: bold;
    }

    .hero p {
      font-size: 1.5rem;
      margin-top: 10px;
    }

    .about h2, .contact h2 {
      font-size: 2rem;
      margin-bottom: 1rem;
    }

    .gallery-container img {
      width: 75%;
      height: auto;
      object-fit: cover;
      border-radius: 10px;
      box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
    }

    .footer {
      background: #222;
      color: white;
      text-align: center;
      padding: 2rem 0;
      width: 100%;
    }
</style>

<section class="hero">
    <h1>The Eliot Quartet</h1>
    <p>Chamber music for your special occasions</p>
</section>

<section class="section about">
    <h2>About Us</h2>
    <p>We are a passionate group of musicians dedicated to bringing beautiful chamber music to a variety of events and occasions.</p>
</section>

<section class="section contact">
    <h2>Contact</h2>
    <p>Request us for your event by emailing us at <a href="mailto:jbejjani@college.harvard.edu">jbejjani@college.harvard.edu</a> or calling +1 (201) 492-1440.</p>
</section>

<div class="gallery-container">
    {#each galleryImages as img}
        <img src={img} alt="Eliot Quartet Performance">
    {/each}
</div>

<footer class="footer">
    <p>&copy; {new Date().getFullYear()} Eliot Quartet. All rights reserved.</p>
</footer>
