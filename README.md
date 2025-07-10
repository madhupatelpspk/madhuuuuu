<div id="now-playing"></div>
<script>
async function fetchNowPlaying() {
  const res = await fetch('https://api.spotify.com/v1/me/player/currently-playing', {
    headers: { 'Authorization': 'Bearer 1POdFZRZbvb...qqillRxMr2z' }
  });
  if (res.status === 200) {
    const data = await res.json();
    document.getElementById('now-playing').innerHTML = `
      <img src="${data.item.album.images[0].url}" width="64"/>
      <strong>${data.item.name}</strong> by ${data.item.artists.map(a => a.name).join(", ")}
    `;
  }
}
setInterval(fetchNowPlaying, 10000);
</script
