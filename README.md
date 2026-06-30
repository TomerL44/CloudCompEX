<h1 id="-green-zebra-orchid-care-system">🌿 Green Zebra - Orchid Care System</h1>
<blockquote>
<p>An AI-powered orchid monitoring and care assistant built as a Google Colab web application.</p>
</blockquote>
<hr>
<h2 id="overview">Overview</h2>
<p><strong>Green Zebra</strong> combines IoT sensor monitoring, computer vision, scientific research retrieval, and generative AI into a single dashboard for orchid care. It runs entirely inside a Google Colab notebook and renders a full interactive web UI using Tailwind CSS and the Colab Output API.</p>
<hr>
<h2 id="features">Features</h2>
<table>
<thead>
<tr>
<th>Feature</th>
<th>Technology</th>
</tr>
</thead>
<tbody>
<tr>
<td>🌡️ Live sensor monitoring (temperature, humidity, soil moisture)</td>
<td>IoT REST API + Firebase Firestore</td>
</tr>
<tr>
<td>🤖 AI-powered care advice</td>
<td>Google Gemini 2.5 Flash</td>
</tr>
<tr>
<td>🌸 Orchid species identification from photos</td>
<td>Vision Transformer (ViT) via Hugging Face</td>
</tr>
<tr>
<td>🔬 Scientific research search</td>
<td>Custom TF-IDF engine + RAG pipeline</td>
</tr>
<tr>
<td>🏆 Care streak tracking &amp; achievement badges</td>
<td>Firebase Firestore</td>
</tr>
<tr>
<td>📈 Hourly sensor trend charts</td>
<td>Matplotlib + Pandas</td>
</tr>
</tbody>
</table>
<hr>
<h2 id="setup">Setup</h2>
<h3 id="prerequisites">Prerequisites</h3>
<ul>
<li>Google account with access to <a href="https://colab.research.google.com">Google Colab</a></li>
<li>A Firebase project with Firestore enabled</li>
<li>A Gemini API key (<a href="https://aistudio.google.com/">get one here</a>)</li>
<li>A Hugging Face account token</li>
</ul>
<h3 id="step-by-step">Step-by-step</h3>
<p><strong>1. Clone or upload the notebook</strong></p>
<p>Upload <code>GreenZebra.ipynb</code> to your Google Drive and open it in Colab.</p>
<p><strong>2. Configure Colab Secrets</strong></p>
<p>Open the <strong>Secrets</strong> panel (🔑 icon in the left sidebar) and add:</p>
<table>
<thead>
<tr>
<th>Secret Name</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>GEMINI_API_KEY</code></td>
<td>Your Google Gemini API key</td>
</tr>
<tr>
<td><code>HF_TOKEN</code></td>
<td>Your Hugging Face access token</td>
</tr>
<tr>
<td><code>FIREBASE_CREDENTIALS</code></td>
<td>Your Firebase JSON</td>
</tr>
</tbody>
</table>
<p><strong>3. Run all cells in order</strong></p>
<pre><code>C<span class="hljs-function"><span class="hljs-title">ell</span> 0 -&gt;</span> C<span class="hljs-function"><span class="hljs-title">ell</span> 1 -&gt;</span> C<span class="hljs-function"><span class="hljs-title">ell</span> 2 -&gt;</span> C<span class="hljs-function"><span class="hljs-title">ell</span> 3 -&gt;</span> C<span class="hljs-function"><span class="hljs-title">ell</span> 4 -&gt;</span> C<span class="hljs-function"><span class="hljs-title">ell</span> 5 -&gt;</span> Cell <span class="hljs-number">6</span>
</code></pre><p>The UI will render automatically after Cell 6 completes.</p>
<p>RUN CELLS 3-5 only once when uploading index!!!</p>
<hr>
<h2 id="application-tabs">Application Tabs</h2>
<h3 id="dashboard">Dashboard</h3>
<p>The main screen. Displays a live <strong>Health Score</strong> (0–100%) calculated from all three sensors, AI-generated care advice, and a gamified care tracker.</p>
<p><strong>Sensor thresholds used for scoring:</strong></p>
<table>
<thead>
<tr>
<th>Sensor</th>
<th>Min</th>
<th>Max</th>
<th>Unit</th>
</tr>
</thead>
<tbody>
<tr>
<td>Temperature</td>
<td>15</td>
<td>30</td>
<td>°C</td>
</tr>
<tr>
<td>Air Humidity</td>
<td>40</td>
<td>70</td>
<td>%</td>
</tr>
<tr>
<td>Soil Moisture</td>
<td>30</td>
<td>70</td>
<td>%</td>
</tr>
</tbody>
</table>
<p><strong>Achievement badges:</strong></p>
<table>
<thead>
<tr>
<th>Badge</th>
<th>Condition</th>
</tr>
</thead>
<tbody>
<tr>
<td>🌱 Sprout</td>
<td>First care log entry</td>
</tr>
<tr>
<td>🌿 Growing</td>
<td>3-day care streak</td>
</tr>
<tr>
<td>🌸 Blooming</td>
<td>7-day care streak</td>
</tr>
<tr>
<td>🏆 Master Grower</td>
<td>30-day care streak</td>
</tr>
</tbody>
</table>
<hr>
<h3 id="orchid-type-scanner">Orchid Type Scanner</h3>
<p>Upload a photo of your orchid and the system will identify its species.</p>
<p><strong>Tips for accurate results:</strong></p>
<ul>
<li>Use natural light, avoid flash</li>
<li>Focus on leaves and roots</li>
<li>Include the whole plant</li>
<li>Avoid heavy shadows</li>
</ul>
<hr>
<h3 id="live-sensors">Live Sensors</h3>
<p>Fetch real-time readings from IoT sensors and view:</p>
<ul>
<li>A table of readings with OK / Out of range status</li>
<li>Summary statistics (average, min, max)</li>
<li>Care recommendations based on current values</li>
<li>An hourly trend chart across all sensors</li>
</ul>
<hr>
<h3 id="research-rag-">Research (RAG)</h3>
<p>Ask questions about orchid care in natural language. The system:</p>
<ol>
<li>Tokenizes and lemmatizes your query</li>
<li>Scores 5 indexed scientific articles using TF-IDF (stored in Firestore)</li>
<li>Selects the top 2 most relevant articles as context</li>
<li>Fetches live sensor readings</li>
<li>Sends everything to Gemini 2.5 Flash for a grounded, cited answer</li>
</ol>
<hr>
<h2 id="data-storage">Data Storage</h2>
<table>
<thead>
<tr>
<th>Data</th>
<th>Firestore Collection</th>
<th>When Saved</th>
</tr>
</thead>
<tbody>
<tr>
<td>TF-IDF index</td>
<td><code>orchid_tfidf</code></td>
<td>Once, during index build</td>
</tr>
<tr>
<td>Sensor readings</td>
<td><code>sensor_readings</code></td>
<td>On every &quot;Fetch readings&quot;</td>
</tr>
<tr>
<td>Care actions</td>
<td><code>care_log</code></td>
<td>On &quot;Watered&quot; / &quot;Checked&quot;</td>
</tr>
</tbody>
</table>
<blockquote>
<p><strong>Photos are never stored.</strong> Images uploaded to the Scanner are processed in-memory and discarded immediately after classification.</p>
</blockquote>
<hr>
<h2 id="tech-stack">Tech Stack</h2>
<table>
<thead>
<tr>
<th>Layer</th>
<th>Technology</th>
</tr>
</thead>
<tbody>
<tr>
<td>Notebook runtime</td>
<td>Google Colab (Python 3)</td>
</tr>
<tr>
<td>UI framework</td>
<td>Tailwind CSS (CDN) + vanilla JavaScript</td>
</tr>
<tr>
<td>Python → JS bridge</td>
<td><code>google.colab.output</code> API</td>
</tr>
<tr>
<td>Database</td>
<td>Firebase Firestore (via <code>firebase-admin</code>)</td>
</tr>
<tr>
<td>IoT data source</td>
<td>Custom REST server on Render.com</td>
</tr>
<tr>
<td>LLM</td>
<td>Google Gemini 2.5 Flash (<code>google-generativeai</code>)</td>
</tr>
<tr>
<td>Image classification</td>
<td>Hugging Face <code>transformers</code> pipeline</td>
</tr>
<tr>
<td>NLP</td>
<td>NLTK (<code>WordNetLemmatizer</code>)</td>
</tr>
<tr>
<td>Charts</td>
<td>Matplotlib + Pandas</td>
</tr>
<tr>
<td>Font</td>
<td>DM Sans (Google Fonts)</td>
</tr>
</tbody>
</table>
<hr>
<h2 id="project-structure">Project Structure</h2>
<pre><code>GreenZebra.ipynb
├── Cell 0  — <span class="hljs-keyword">Install</span> dependencies &amp; NLTK <span class="hljs-keyword">data</span>
├── Cell <span class="hljs-number">1</span>  — Firebase <span class="hljs-keyword">authentication</span> &amp; Firestore <span class="hljs-keyword">client</span>
├── Cell <span class="hljs-number">2</span>  — Download <span class="hljs-number">5</span> research articles <span class="hljs-keyword">from</span> Google Drive
├── Cell <span class="hljs-number">3</span>  — <span class="hljs-keyword">Define</span> <span class="hljs-keyword">stop</span> words
├── Cell <span class="hljs-number">4</span>  — <span class="hljs-keyword">Build</span> TF-IDF <span class="hljs-keyword">index</span> <span class="hljs-keyword">in</span> <span class="hljs-keyword">memory</span>
├── Cell <span class="hljs-number">5</span>  — Upload TF-IDF <span class="hljs-keyword">index</span> <span class="hljs-keyword">to</span> Firestore
└── Cell <span class="hljs-number">6</span>  — <span class="hljs-keyword">Main</span> application (UI + all callbacks)
    ├── Configuration (THRESHOLDS, ALERTS, ADVICE, BADGES_DEF)
    ├── Sensor tab helpers
    ├── Dashboard tab helpers
    ├── RAG pipeline (_build_rag)
    ├── Chart builder (_build_chart)
    ├── Orchid scanner (cb_scan_orchid)
    ├── Callback registrations
    └── HTML/JS UI (APP_HTML)
</code></pre><hr>
<h2 id="security-considerations">Security Considerations</h2>
<ul>
<li>Store all credentials (<code>GEMINI_API_KEY</code>, <code>HF_TOKEN</code>, Firebase service account) in <strong>Colab Secrets</strong>, not in notebook cells.</li>
<li>Firebase Private Keys embedded directly in code should be <strong>rotated immediately</strong> if accidentally committed to a public repository.</li>
<li>The <code>_md_to_html</code> function sanitizes Gemini output (HTML-escapes <code>&amp;</code>, <code>&lt;</code>, <code>&gt;</code>) before injecting into the DOM to prevent XSS.</li>
</ul>
<hr>
<h2 id="license">License</h2>
<p>Authored by:
 Daniil Hessen, Tedy Haddad, Leon Sigal, Yarin Hammami, Tomer Levy</p>
