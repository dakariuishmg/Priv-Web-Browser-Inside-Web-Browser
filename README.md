# Priv-Web-Browser-Inside-Web-Browser
A private web browser designed to be ran within any web browser, google, firefox, brave, etc, with onion considerations. This foundation will allow developers to create a private portal to browse the internet with zero tracking as well as give their Local AI Agents true Sovereign Internet+.

# UISH

**UISH** (Universal Interface Single HTML) is a high-performance web browser interface built entirely in a single HTML file. It delivers advanced browsing capabilities including multi-tab support, reader mode, proxy racing with EWMA optimization, double-buffered rendering, and intelligent LRU caching—all without external dependencies.

## Features

- **Single File Architecture**: Everything packed into one HTML file for maximum portability
- **Multi-Tab Support**: Full-featured tab management with session persistence
- **Reader Mode**: Clean, distraction-free reading experience with text extraction
- **Proxy Racing**: Automatic proxy selection using EWMA (Exponentially Weighted Moving Average)
- **Double-Buffered Rendering**: Smooth page transitions without visual artifacts
- **LRU Cache**: Intelligent caching system for optimal performance
- **Web Workers**: Offloaded processing for responsive UI
- **MessageChannel API**: Efficient inter-worker communication
- **Session Persistence**: Save and restore browsing sessions
- **Privacy Focused**: No external tracking or analytics

## Installation

### Option 1: Direct Download

1. Download `uish.html` from this repository
2. Open the file in any modern web browser
3. Start browsing!

### Option 2: Clone Repository

```bash
git clone https://github.com/yourusername/uish.git
cd uish
```

Then open `uish.html` in your browser.

### Option 3: Serve Locally

For full functionality (Web Workers, CORS), serve via HTTP:

```bash
# Using Python 3
python -m http.server 8000

# Using Node.js (http-server)
npx http-server -p 8000

# Using PHP
php -S localhost:8000
```

Then navigate to `http://localhost:8000/uish.html`

## Usage

### Basic Navigation

1. **Open UISH**: Launch `uish.html` in your browser
2. **Enter URL**: Type or paste a URL in the address bar
3. **Browse**: Navigate web pages through the proxy interface

### Tab Management

- **New Tab**: Click the `+` button or use keyboard shortcut
- **Switch Tabs**: Click on tab headers
- **Close Tab**: Click the `×` on the tab you want to close
- **Reorder Tabs**: Drag and drop tab headers (if enabled)

### Reader Mode

1. Navigate to any article or content page
2. Click the **Reader Mode** button in the toolbar
3. Enjoy clean, formatted text without distractions
4. Click again to return to normal view

### Proxy Configuration

UIsh automatically races between multiple proxy endpoints and selects the fastest using EWMA:

- Proxies are evaluated on each request
- Response times are tracked with exponential weighting
- Fastest proxy is automatically selected
- Failed proxies are temporarily blacklisted

### Advanced Features

**Session Persistence**
- Sessions are automatically saved to localStorage
- Restore previous session on startup
- Manual session export/import (if implemented)

**Cache Management**
- LRU cache automatically manages memory
- Configurable cache size limits
- Manual cache clearing available

**Performance Monitoring**
- Built-in performance metrics
- Proxy latency tracking
- Memory usage indicators

## Configuration

Edit the configuration section in `uish.html` to customize:

```javascript
const CONFIG = {
  maxTabs: 20,
  cacheSize: 100,
  proxyTimeout: 5000,
  ewmaAlpha: 0.3,
  enableReaderMode: true,
  enableDoubleBuffer: true,
  proxies: [
    'https://proxy1.example.com',
    'https://proxy2.example.com'
  ]
};
```

## Technical Architecture

### Core Components

- **Main Thread**: UI rendering and user interaction
- **Web Workers**: Background processing and proxy requests
- **MessageChannel**: Worker-to-worker communication
- **IndexedDB/localStorage**: Session and cache persistence
- **Double Buffer**: Offscreen canvas for smooth rendering

### Performance Optimizations

- **EWMA Proxy Selection**: Intelligent proxy routing based on historical performance
- **LRU Cache**: Least Recently Used eviction for memory efficiency
- **Lazy Loading**: Deferred loading of non-critical resources
- **Request Coalescing**: Batched requests for reduced overhead
- **Virtual Scrolling**: Efficient rendering of large content

### Security Considerations

- All external content is proxied
- CSP headers enforced where possible
- XSS protection through content sanitization
- No third-party scripts or tracking
- Sandboxed iframe rendering

## Browser Compatibility

UIsh requires a modern browser with support for:

- ES6+ JavaScript
- Web Workers
- MessageChannel API
- localStorage/IndexedDB
- CSS Grid and Flexbox

**Tested on:**
- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Opera 76+

## Requirements

- Modern web browser (Chrome, Firefox, Safari, Edge)
- JavaScript enabled
- localStorage enabled (for session persistence)
- Minimum 2GB RAM recommended
- Internet connection for proxy access

## Performance Tips

1. **Limit Open Tabs**: Keep active tabs under 10 for best performance
2. **Clear Cache**: Periodically clear cache if memory usage is high
3. **Use Reader Mode**: For text-heavy content, reader mode is faster
4. **Configure Proxies**: Add multiple proxy endpoints for better racing results
5. **Disable Features**: Turn off unused features in configuration

## Troubleshooting

### Proxy Not Working
- Check proxy URLs in configuration
- Verify internet connection
- Check browser console for errors
- Try different proxy endpoints

### Performance Issues
- Clear browser cache
- Reduce number of open tabs
- Lower cache size in configuration
- Disable double-buffering if needed

### Reader Mode Not Activating
- Ensure page has sufficient text content
- Check that reader mode is enabled in config
- Try refreshing the page

## Contributing

Contributions are welcome! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines

- Maintain single-file architecture
- Keep dependencies minimal (preferably zero)
- Write clean, documented code
- Test across multiple browsers
- Update README for new features

## Roadmap

- [ ] Bookmarks management
- [ ] History tracking with search
- [ ] Extensions/plugins system
- [ ] Themes and customization
- [ ] Mobile responsive design
- [ ] PWA support
- [ ] Ad blocking capabilities
- [ ] Download manager
- [ ] Privacy mode
- [ ] Sync across devices

## Known Issues

- Some websites may not render correctly through proxy
- CORS restrictions may limit certain features
- Heavy JavaScript sites may experience performance degradation
- Reader mode extraction may fail on complex layouts

## License

MIT License

Copyright (c) 2024 UISH Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Acknowledgments

- Inspired by modern web browser architectures
- EWMA algorithm based on TCP congestion control
- Reader mode extraction inspired by Mozilla Readability
- LRU cache implementation optimized for web context

## Support

For issues, questions, or suggestions:

- Open an issue on GitHub
- Check existing issues for solutions
- Review documentation and FAQs

## Disclaimer

UIsh is provided as-is for educational and personal use. The proxy functionality should be used responsibly and in accordance with applicable laws and terms of service. The authors are not responsible for misuse or any damages resulting from the use of this software.

---

**Made with ❤️ by the UISH community**
