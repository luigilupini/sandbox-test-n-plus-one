## Next.js performance testing
> 1. open client folder

```bash
npm run dev
```

> 2. open express-api folder

```bash
node index.js
```

> 3. install oha (https://github.com/hatoo/oha)

```bash
brew install oha
```

> 4. open terminal to measure response time oha

```bash
oha -z 10s http://localhost:3000/1-aggregated-client
oha -z 10s http://localhost:3000/2-aggregated-server
oha -z 10s http://localhost:3000/2-n-plus-one-isr
oha -z 10s http://localhost:3000/2-n-plus-one-ssg
oha -z 10s http://localhost:3000/2-n-plus-one-ssr
```

| n-plus-one (ssg) | Summary |
Success rate: 100.00%
Total: 10.0018 secs
Slowest: 9.7183 secs
Fastest: 0.5082 secs
Average: 5.6465 secs
Requests/sec: 5.0991

Total data: 324.08 KiB
Size/request: 6.35 KiB
Size/sec: 32.40 KiB

| n-plus-one (isr) | Summary |
Success rate: 100.00%
Total: 10.0014 secs
Slowest: 9.7313 secs
Fastest: 1.6015 secs
Average: 5.7258 secs
Requests/sec: 5.0993

Total data: 324.11 KiB
Size/request: 6.35 KiB
Size/sec: 32.41 KiB

> 5. open tester folder to see size of html, json, client-json payloads

```bash
node index.js http://localhost:3000/1-aggregated-client
node index.js http://localhost:3000/2-aggregated-server
node index.js http://localhost:3000/2-n-plus-one-isr
node index.js http://localhost:3000/2-n-plus-one-ssg
node index.js http://localhost:3000/2-n-plus-one-ssr
```

http://localhost:3000/1-aggregated-client
HTML: 71.59 KB - 42.4%
JSON: 97.23 KB - 57.6%
JSON Client Data: 75.26 KB - 77.4%
http://localhost:3000/2-aggregated-server
HTML: 0.77 KB - 10.7%
JSON: 6.37 KB - 89.3%
JSON Client Data: 0.00 KB - 0.0%
http://localhost:3000/2-n-plus-one-isr
HTML: 72.69 KB - 44.8%
JSON: 89.50 KB - 55.2%
JSON Client Data: 0.00 KB - 0.0%
http://localhost:3000/2-n-plus-one-ssg
HTML: 72.69 KB - 44.8%
JSON: 89.50 KB - 55.2%
JSON Client Data: 0.00 KB - 0.0%
http://localhost:3000/2-n-plus-one-ssr
HTML: 72.69 KB - 44.8%
JSON: 89.50 KB - 55.2%
JSON Client Data: 0.00 KB - 0.0%
