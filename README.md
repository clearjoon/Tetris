# Tetris
<!-- 
  ====================================================================
  TETRIS GAME TRIGGER COMPONENT
  ====================================================================
  Instructions:
  1. Copy and paste this snippet into your existing website (e.g., index.html).
  2. Replace the 'href' value in the JavaScript or anchor tag with your actual 
     GitHub Pages URL (e.g., 'https://username.github.io/repository-name/tetris.html').
-->

<!-- Tailwind CSS is used for structure. Custom CSS below handles the premium neon animations. -->
<style>
  @keyframes neon-pulse {
    0%, 100% {
      box-shadow: 0 0 8px rgba(0, 230, 118, 0.4), 0 0 20px rgba(0, 230, 118, 0.2);
    }
    50% {
      box-shadow: 0 0 15px rgba(0, 230, 118, 0.7), 0 0 30px rgba(0, 230, 118, 0.4);
    }
  }

  .tetris-btn-glow {
    position: relative;
    overflow: hidden;
    transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    background: linear-gradient(135deg, #0f0f16 0%, #1c1c28 100%);
    border: 2px solid #00e676;
  }

  .tetris-btn-glow:hover {
    transform: translateY(-4px) scale(1.03);
    color: #ffffff;
    animation: neon-pulse 1.5s infinite;
    border-color: #00e5ff; /* Shifts to cyan on hover */
  }

  /* Shimmer shine reflection effect */
  .tetris-btn-glow::after {
    content: '';
    position: absolute;
    top: 0;
    left: -150%;
    width: 50%;
    height: 100%;
    background: linear-gradient(
      to right,
      rgba(255, 255, 255, 0) 0%,
      rgba(255, 255, 255, 0.13) 50%,
      rgba(255, 255, 255, 0) 100%
    );
    transform: skewX(-25deg);
    transition: 0.75s;
  }

  .tetris-btn-glow:hover::after {
    left: 150%;
    transition: 0.75s ease-in-out;
  }

  /* Rotating Tetris block decor shapes */
  .block-decor {
    transition: transform 0.6s ease;
  }
  .tetris-btn-glow:hover .block-decor {
    transform: rotate(90deg);
  }
</style>

<div class="flex items-center justify-center p-6">
  <!-- Trigger Anchor / Button -->
  <a 
    id="tetrisTriggerLink"
    href="tetris.html" 
    class="tetris-btn-glow group flex items-center justify-between gap-4 px-6 py-4 rounded-xl text-slate-100 font-bold tracking-wider shadow-lg max-w-sm w-full cursor-pointer decoration-transparent"
  >
    <!-- Left Icon (Tetris T-Shape) -->
    <svg class="block-decor w-6 h-6 fill-[#00e676] group-hover:fill-[#00e5ff] transition-colors duration-300" viewBox="0 0 24 24">
      <!-- T-Shape Blocks -->
      <path d="M2,9 H8 V15 H2 Z M8,9 H14 V15 H8 Z M14,9 H20 V15 H14 Z M8,3 H14 V9 H8 Z" />
    </svg>

    <!-- Center Call-to-Action Text -->
    <div class="flex flex-col items-start leading-tight">
      <span class="text-xs tracking-widest text-[#aaaab4] group-hover:text-white uppercase font-black transition-colors duration-300">Play Retro Classic</span>
      <span class="text-md font-extrabold group-hover:text-[#00e5ff] transition-colors duration-300">Play Tetris Now 🕹️</span>
    </div>

    <!-- Right Indicator (Arrow) -->
    <svg class="w-5 h-5 stroke-[#aaaab4] group-hover:stroke-[#00e5ff] group-hover:translate-x-1 transition-all duration-300" fill="none" stroke-width="2.5" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
    </svg>
  </a>
</div>

<script>
  /**
   * Safe Routing Handler for GitHub Pages
   * Detects local development vs production deployment environment
   */
  document.getElementById('tetrisTriggerLink').addEventListener('click', function(e) {
    e.preventDefault();
    
    // Default fallback path for GitHub Pages relative structures
    let destination = 'tetris.html'; 
    
    // Example of absolute GitHub Pages fallback targeting (Uncomment and customize if needed)
    // const isGitHubPages = window.location.hostname.includes('github.io');
    // if (isGitHubPages) {
    //   const pathArray = window.location.pathname.split('/');
    //   const repoName = pathArray[1]; // Gets 'repository-name'
    //   destination = `/${repoName}/tetris.html`;
    // }

    // Execute smooth page-out transition before redirecting
    document.body.style.opacity = '0';
    document.body.style.transition = 'opacity 0.4s ease';
    
    setTimeout(() => {
      window.location.href = destination;
    }, 350);
  });
</script>
