<html>
<head>
<title> Dashboard </title>
<script src="purify.min.js"></script>
</head>
<body>
    <h1>Dashboard</h1>

    <p> <span id="name">Guest</span>, Welcome to the Dashboard
    <a href="logout">Logout</a>
    </p>
    <p> <a href="profile">Profile</a> <span id="profileComment"></span></p>
    <p> <a href="settings">Settings</a> <span id="settingsComment"></span></p>
    <p> <a href="points">Points</a> (<span id="points">0</span>)</p>
    <p> <a href="leaderboard">Leaderboard</a></p>
</body>
<script>
    const urlParams = new URLSearchParams(window.location.search);
    for (var [key, value] of urlParams) {
        if(document.getElementById(key)) {
            document.getElementById(key).innerText = `${value}`;
        } else if (window.debugMode) {
            document.write("unidentified keys <br/>");
            document.write(`${key} = ${value} <br/>`);
        } else {
            key = DOMPurify.sanitize(key);
            document.write(`<span style='color: red'>${key} not found in the document</span><br/>`);
        }
    }
</script>
</html>
