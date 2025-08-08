# Notebook

<!DOCTYPE html>
<html>
<head>
<title>Docs Viewer</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
body {
  margin: 0;
  font-family: sans-serif;
  background: #f4f4f4;
}
header {
  background: #333;
  color: #fff;
  padding: 10px;
  text-align: center;
  font-size: 18px;
}
form {
  margin: 10px;
  display: flex;
}
input[type="text"] {
  flex: 1;
  padding: 8px;
  border: none;
  border-radius: 4px 0 0 4px;
}
button {
  padding: 8px 12px;
  border: none;
  background: #4CAF50;
  color: white;
  border-radius: 0 4px 4px 0;
}
iframe {
  width: 100%;
  height: calc(100vh - 100px);
  border: none;
}
</style>
</head>
<body>
<header>Documentation Portal</header>

<form id="proxyForm">
  <input type="text" id="url" placeholder="Enter website URL">
  <button type="submit">Go</button>
</form>

<iframe id="viewer"></iframe>

<script>
document.getElementById('proxyForm').addEventListener('submit', function(e) {
  e.preventDefault();
  let site = document.getElementById('url').value.trim();
  if (!site.startsWith('http://') && !site.startsWith('https://')) {
    site = 'https://' + site;
  }
  // Send through a hidden proxy endpoint
  const proxy = 'https://corsproxy.io/?' + encodeURIComponent(site);
  document.getElementById('viewer').src = proxy;
});
</script>

</body>
</html>
