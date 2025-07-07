<button id="toggle-btn">Toggle Dark Mode</button>

<style>
  body {
    background-color: white;
    color: black;
    transition: background-color 0.3s, color 0.3s;
  }

  body.dark-mode {
    background-color: #121212;
    color: #e0e0e0;
  }

  #toggle-btn {
    margin: 1em 0;
    padding: 0.5em 1em;
    cursor: pointer;
  }
</style>

<script>
  const toggleBtn = document.getElementById('toggle-btn');
  const body = document.body;

  // Load saved mode from localStorage, if any
  const savedMode = localStorage.getItem('darkMode');

  if (savedMode === 'enabled') {
    body.classList.add('dark-mode');
  }

  toggleBtn.addEventListener('click', () => {
    body.classList.toggle('dark-mode');

    // Save preference in localStorage
    if (body.classList.contains('dark-mode')) {
      localStorage.setItem('darkMode', 'enabled');
    } else {
      localStorage.setItem('darkMode', 'disabled');
    }
  });
</script>

# Posts: 

 - [Decrypting a Malware](/docs/Malware-analysis.md#malware-analysis)

# Social:
 - 
