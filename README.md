# Cric<!DOCTYPE html><html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IPL Live Score</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; }
        .scoreboard { margin-top: 20px; padding: 10px; border: 1px solid #ccc; display: inline-block; }
    </style>
</head>
<body>
    <h1>IPL & Cricket Live Scores</h1>
    <div id="liveScore" class="scoreboard">Fetching live scores...</div><script>
    async function fetchLiveScore() {
        try {
            let response = await fetch('https://api.cricapi.com/v1/cricScore?apikey=aaa51e3f-faab-44e5-bb49-5fb52b454260');
            let data = await response.json();
            document.getElementById('liveScore').innerHTML = data.matches.map(match => 
                `<p>${match.team1} vs ${match.team2}: ${match.score}</p>`).join('');
        } catch (error) {
            document.getElementById('liveScore').innerHTML = "Error fetching live scores.";
        }
    }
    
    fetchLiveScore();
    setInterval(fetchLiveScore, 60000); // Refresh every minute
</script>

</body>
</html>