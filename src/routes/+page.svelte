<script>
  const projects = [
    {
      title: "How Same Or Different Are We",
      image: "/howSameOrDifferentAreWe.png",
      link: "https://capstone-wine-kappa.vercel.app/",
    },
    {
      title: "Visualizing My Mind",
      image: "/visualizingMyMind.png",
      link: "https://visualizing-my-mind.vercel.app/",
    },
    // {
    //   title: "How Same Or Different Are We",
    //   image: "/howSameOrDifferentAreWe.png",
    //   link: "https://capstone-wine-kappa.vercel.app/",
    // },
  ];

  let x = 0;
  let y = 0;
  let hoveringCard = false;

  const handleMouseMove = (/** @type {MouseEvent} */ event) => {
    x = event.clientX;
    y = event.clientY;
  };

  const setHover = () => (hoveringCard = true);
  const unsetHover = () => (hoveringCard = false);
</script>

<svelte:window on:mousemove={handleMouseMove} />

<div class="container">
  <!-- <h1>Hi! I'm Vaishali Verma.</h1>
  <h1>I design and develop mostly with data</h1>
  <h1>
    Working with foundational AI models, into experimenting with latest
    techniques to augment experiences with LLMs
  </h1> -->
  <h3>Hi! I'm Vaishali Verma.</h3>
  <div>I design and develop mostly with data</div>
  <div>
    Officially, I’m mostly a data visualization designer and developer OR a
    product designer depending on how you define roles within your company.
  </div>
  <div>
    I prototype zero-to-one design solutions to code using HTML/CSS/JS/Python,
    not just static mockups. This reduces overall risk by validating what’s
    possible, where we run against the limitations of tech or what design
    decisions need revisiting.
  </div>
  <div>
    Recently, I have started experimenting with AI Agents trying to understand
    the weakness and strengths of using LLMs to solve domain specific problems.
  </div>

  <div class="card-container">
    {#each projects as project}
      <a
        href={project.link}
        target="_blank"
        rel="noopener"
        class="card"
        on:mouseenter={setHover}
        on:mouseleave={unsetHover}
      >
        <img src={project.image} alt={project.title} />
        <div class="card-title">{project.title}</div>
      </a>
    {/each}
  </div>
</div>

<!-- Custom circle cursor -->
<div
  class="custom-cursor {hoveringCard ? 'hover' : ''}"
  style="left: {x}px; top: {y}px;"
>
  {#if hoveringCard}
    <span class="cursor-text">VIEW</span>
  {/if}
</div>

<style>
  /* Hide the default pointer everywhere */
  :global(body),
  :global(a),
  :global(.card),
  :global(button) {
    cursor: none;
  }

  .custom-cursor {
    position: fixed;
    width: 16px;
    height: 16px;
    background: black;
    border-radius: 50%;
    pointer-events: none;
    transform: translate(-50%, -50%);
    z-index: 1000;
    transition:
      width 0.2s ease,
      height 0.2s ease,
      background 0.2s ease;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: sans-serif;
    color: white;
    font-size: 0.75rem;
  }

  .custom-cursor.hover {
    width: 60px;
    height: 60px;
  }

  .cursor-text {
    color: white;
    font-weight: bold;
    font-size: 0.75rem;
    user-select: none;
    pointer-events: none;
  }

  .container {
    height: 100vh;
    max-width: 1000px;
    padding-top: 33vh;
    text-align: center;
    font-family: sans-serif;
  }

  h3 {
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
    width: 450px;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    text-align: center;
    background: white;
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
