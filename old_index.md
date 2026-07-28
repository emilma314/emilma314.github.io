---
layout: home
title: Emil Ma
---

# Hi, I'm Emil

I'm <span id="age-display">18</span> years old.

<script>
function updateAge() {
  const birthDate = new Date('2008-02-13T00:00:00');
  const now = new Date();
  const msPerYear = 1000 * 60 * 60 * 24 * 365.25;
  const ageDecimal = (now - birthDate) / msPerYear;
  document.getElementById('age-display').innerText = ageDecimal.toFixed(6);
}
updateAge();
setInterval(updateAge, 100);
</script>

## Music
[embed videos]

## Work
work

## Chess
<div id="chess-stats">Loading chess.com ratings...</div>
<script>
fetch('https://api.chess.com/pub/player/limeboi314159/stats')
  .then(res => res.json())
  .then(data => {
    const rapid = data.chess_rapid?.last?.rating ?? 'N/A';
    const blitz = data.chess_blitz?.last?.rating ?? 'N/A';
    const bullet = data.chess_bullet?.last?.rating ?? 'N/A';
    document.getElementById('chess-stats').innerHTML = `
      <ul>
        <li><strong>Rapid:</strong> ${rapid}</li>
        <li><strong>Blitz:</strong> ${blitz}</li>
        <li><strong>Bullet:</strong> ${bullet}</li>
      </ul>
    `;
  })
  .catch(() => {
    document.getElementById('chess-stats').innerText = 'Could not load chess.com stats.';
  });
</script>