<svg xmlns="http://www.w3.org/2000/svg" width="1000" height="350" viewBox="0 0 1000 350">
  <defs>
    <!-- Psychedelic tie-dye gradient -->
    <radialGradient id="tieDye" cx="50%" cy="50%" r="80%" fx="20%" fy="20%">
      <stop offset="0%" stop-color="#ff00ff"/>
      <stop offset="20%" stop-color="#ff6600"/>
      <stop offset="40%" stop-color="#ffff00"/>
      <stop offset="60%" stop-color="#00ff99"/>
      <stop offset="80%" stop-color="#0066ff"/>
      <stop offset="100%" stop-color="#9900ff"/>
    </radialGradient>

    <!-- Flowing distortion filter -->
    <filter id="flow" x="0%" y="0%" width="100%" height="100%">
      <feTurbulence type="turbulence" baseFrequency="0.01 0.02" numOctaves="3" seed="7" result="noise">
        <animate attributeName="baseFrequency" dur="10s"
                 values="0.01 0.02;0.03 0.05;0.01 0.02" repeatCount="indefinite"/>
      </feTurbulence>
      <feDisplacementMap in="SourceGraphic" in2="noise" scale="50"/>
    </filter>
  </defs>

  <!-- GitHub background color -->
  <rect width="100%" height="100%" fill="#0d1117"/>

  <!-- AES Main Text -->
  <text x="50%" y="45%" text-anchor="middle" dominant-baseline="middle"
        font-family="Impact, sans-serif" font-size="200"
        fill="url(#tieDye)" filter="url(#flow)"
        stroke="#fff" stroke-width="6" paint-order="stroke">
    AES
  </text>
  <!-- Outer black stroke -->
  <text x="50%" y="45%" text-anchor="middle" dominant-baseline="middle"
        font-family="Impact, sans-serif" font-size="200"
        fill="none" stroke="#000" stroke-width="10" paint-order="stroke">
    AES
  </text>

  <!-- Subheadline -->
  <text x="50%" y="70%" text-anchor="middle"
        font-family="Arial, sans-serif" font-size="40"
        fill="#e6edf3">
    Arbitrage Execution System
  </text>

  <!-- Extra Info Line -->
  <text x="50%" y="82%" text-anchor="middle"
        font-family="Courier New, monospace" font-size="20"
        fill="#8b949e">
    v3.1.4 • Ethereum Mainnet • Token-agnostic, ML-driven, Exchange-neutral
  </text>
</svg>
