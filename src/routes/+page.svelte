<script>
  const projects = [
    {
      title: "How Same Or Different Are We",
      image: "/howSameOrDifferentAreWe.png",
      link: "https://capstone-wine-kappa.vercel.app/",
    },
    {
      title: "How Same Or Different Are We",
      image: "/howSameOrDifferentAreWe.png",
      link: "https://capstone-wine-kappa.vercel.app/",
    },
  ];
  let x = 0;
  let y = 0;

  const handleMouseMove = (/** @type {MouseEvent} */ event) => {
    x = event.clientX;
    y = event.clientY;
  };
</script>

<svelte:window on:mousemove={handleMouseMove} />

<div class="container">
  <h1>Hi! I'm Vaishali Verma.</h1>
  <h1>I design and develop mostly with data</h1>
  <div class="card-container">
    {#each projects as project}
      <a href={project.link} target="_blank" rel="noopener" class="card">
        <img src={project.image} alt={project.title} />
        <div class="card-title">{project.title}</div>
      </a>
    {/each}
  </div>
</div>

<!-- Custom circle cursor -->
<div class="custom-cursor" style="left: {x}px; top: {y}px;"></div>

<style>
  /* Hide the default cursor */
  :global(body) {
    cursor: none;
  }

  .custom-cursor {
    position: fixed;
    width: 16px;
    height: 16px;
    background: black;
    border-radius: 50%;
    pointer-events: none; /* Allows clicking through it */
    transform: translate(-50%, -50%);
    z-index: 1000;
  }

  .container {
    height: 100vh;
    padding-top: 33vh;
    text-align: center;
  }

  h1 {
    margin: 0.5rem 0;
  }
  .card-container {
    display: flex;
    justify-content: center;
    gap: 2rem;
    flex-wrap: wrap;
    margin-top: 3rem;
  }

  .card {
    width: 300px;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    text-align: center;
    background: white;
    cursor: pointer;
    transition: transform 0.2s ease;
    text-decoration: none;
    color: inherit;
  }

  .card:hover {
    transform: scale(1.03);
  }

  .card img {
    width: 100%;
    height: auto;
    display: block;
  }

  .card-title {
    font-size: 1.1rem;
    padding: 1rem;
    font-weight: bold;
  }
</style>
