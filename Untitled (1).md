# OAuth2 redirect_uri mismatch error

Session file:

```text
C:\Users\135324\.dsh\sessions\--D-doc-dsh_workspace--\session-e1b3cf1f-1115-4ac3-9b52-d2acdafa5fa7\session.v4.jsonl.zstd
```

> The OAuth2 request resulted in an error.
> Error: invalid_request
> Description: The request is missing a required parameter, includes an invalid parameter value, includes a parameter more than once, or is otherwise malformed. The 'redirect_uri' parameter does not match any of the OAuth 2.0 Client's pre-registered redirect urls.
> Hint:
> Debug:
> You are seeing this page because configuration key urls.error is not set.
>
> If you are an administrator, please read the guide to understand what you need to do. If you are a user, please contact the administrator.

129 previous messages

**Tool:** `pwsh`

```json
{
  "command": "Get-ChildItem -Force | Select-Object Mode,LastWriteTime,Length,Name | Format-Table -AutoSize",
  "description": "List workspace root contents"
}
```

**Result**

```

Mode   LastWriteTime       Length Name                                     
----   -------------       ------ ----                                     
d----- 2026-11-06 12:37:57        .asar-extract                            
d----- 2026-11-06 20:16:26        .tmp_sessions                            
d----- 2026-11-04 22:08:34        codeg_scan                               
d----- 2026-11-06 21:17:27        _tmp_dshops                              
-a---- 2026-11-06 18:11:58 1056   codex_probe.mjs                          
-a---- 2026-11-06 18:14:04 1971   codex_probe2.mjs                         
-a---- 2026-11-06 18:16:40 794    codex_probe3.mjs                         
-a---- 2026-11-06 18:26:46 445    codex_probe4.mjs                         
-a---- 2026-11-06 14:17:28 50951  codex_session_01a187b4_assistant.txt     
-a---- 2026-11-06 14:17:57 20324  codex_session_01a187b4_assistant_head.txt
-a---- 2026-11-06 14:16:41 12300  codex_session_01a187b4_summary.txt       
-a---- 2026-11-06 14:17:01 6770   codex_session_01a187b4_tail.txt          
-a---- 2026-11-06 10:33:43 41239  elk_waybill_depot_dedup_1000.csv         
-a---- 2026-11-06 10:19:38 41087  elk_waybill_depot_first1000.csv          
-a---- 2026-11-07 0:33:31  1933   _codex_probe.py                          
-a---- 2026-11-07 0:38:09  937    _codex_probe10.py                        
-a---- 2026-11-07 0:38:32  2330   _codex_probe11.py                        
-a---- 2026-11-07 0:38:53  806    _codex_probe12.py                        
-a---- 2026-11-07 0:39:13  919    _codex_probe13.py                        
-a---- 2026-11-07 0:39:37  1248   _codex_probe14.py                        
-a---- 2026-11-07 0:39:50  576    _codex_probe15.py                        
-a---- 2026-11-07 0:40:10  2603   _codex_probe16.py                        
-a---- 2026-11-07 0:41:03  1166   _codex_probe17.py                        
-a---- 2026-11-07 0:41:21  1832   _codex_probe18.py                        
-a---- 2026-11-07 0:42:08  2850   _codex_probe19.py                        
-a---- 2026-11-07 0:33:53  616    _codex_probe2.py                         
-a---- 2026-11-07 0:48:05  1916   _codex_probe20.py                        
-a---- 2026-11-07 0:49:51  2282   _codex_probe21.py                        
-a---- 2026-11-07 0:49:26  504    _codex_probe22.py                        
-a---- 2026-11-07 0:49:35  335    _codex_probe23.py                        
-a---- 2026-11-07 0:50:13  1286   _codex_probe24.py                        
-a---- 2026-11-07 0:50:24  1074   _codex_probe25.py                        
-a---- 2026-11-07 0:51:07  598    _codex_probe26.py                        
-a---- 2026-11-07 0:52:28  2204   _codex_probe27.py                        
-a---- 2026-11-07 0:52:46  510    _codex_probe28.py                        
-a---- 2026-11-07 0:53:43  546    _codex_probe29.py                        
-a---- 2026-11-07 0:34:22  432    _codex_probe3.py                         
-a---- 2026-11-07 0:54:39  2320   _codex_probe30.py                        
-a---- 2026-11-07 13:08:30 2449   _codex_probe31.py                        
-a---- 2026-11-07 13:09:01 2168   _codex_probe32.py                        
-a---- 2026-11-07 0:34:33  870    _codex_probe4.py                         
-a---- 2026-11-07 0:34:54  780    _codex_probe5.py                         
-a---- 2026-11-07 0:35:38  2036   _codex_probe6.py                         
-a---- 2026-11-07 0:36:13  1207   _codex_probe7.py                         
-a---- 2026-11-07 0:36:25  1189   _codex_probe8.py                         
-a---- 2026-11-07 0:36:35  639    _codex_probe9.py                         
-a---- 2026-11-07 0:43:25  458    _ocx_probe1.py                           
-a---- 2026-11-07 0:47:10  1528   _ocx_probe10.py                          
-a---- 2026-11-07 0:47:29  1295   _ocx_probe11.py                          
-a---- 2026-11-07 0:51:35  1379   _ocx_probe12.py                          
-a---- 2026-11-07 0:53:18  2193   _ocx_probe13.py                          
-a---- 2026-11-07 0:54:08  1787   _ocx_probe14.py                          
-a---- 2026-11-07 0:55:00  1420   _ocx_probe15.py                          
-a---- 2026-11-07 0:55:36  1344   _ocx_probe16.py                          
-a---- 2026-11-07 0:55:56  1355   _ocx_probe17.py                          
-a---- 2026-11-07 0:56:20  1896   _ocx_probe18.py                          
-a---- 2026-11-07 0:57:00  2350   _ocx_probe19.py                          
-a---- 2026-11-07 0:43:45  1942   _ocx_probe2.py                           
-a---- 2026-11-07 0:57:38  2003   _ocx_probe20.py                          
-a---- 2026-11-07 0:57:53  1379   _ocx_probe21.py                          
-a---- 2026-11-07 0:44:19  1958   _ocx_probe3.py                           
-a---- 2026-11-07 0:45:00  2193   _ocx_probe4.py                           
-a---- 2026-11-07 0:45:24  835    _ocx_probe5.py                           
-a---- 2026-11-07 0:45:48  1596   _ocx_probe6.py                           
-a---- 2026-11-07 0:46:15  486    _ocx_probe7.py                           
-a---- 2026-11-07 0:46:30  1264   _ocx_probe8.py                           
-a---- 2026-11-07 0:46:45  1280   _ocx_probe9.py                           


```

**Tool:** `glob`

```json
{
  "pattern": "**/*.{yaml,yml,json,env,conf,toml}",
  "path": "D:\\doc\\dsh_workspace"
}
```

**Result**

```
codeg_scan\cleanup-hkcu-result-20261104-220831.json
.asar-extract\dsh\node_modules\@deepseek-ai\dsh-agent-instructions\package.json
_tmp_dshops\i714.json
_tmp_dshops\i714c.json
_tmp_dshops\i709.json
```

**Tool:** `read`

```json
{
  "file_path": "D:\\doc\\dsh_workspace\\_codex_probe32.py"
}
```

**Result**

```
<path>D:\doc\dsh_workspace\_codex_probe32.py</path>
<type>file</type>
<content>
1: import sqlite3, re, datetime, statistics as st
2: from collections import defaultdict, Counter
3: 
4: TZ = datetime.timezone(datetime.timedelta(hours=8))
5: con = sqlite3.connect(r'file:C:\Users\135324\.codex\logs_2.sqlite?mode=ro', uri=True)
6: cur = con.cursor()
7: 
8: # 1) session baseline: first request's input tokens per thread (from usage.jsonl instead)
9: import json
10: recs = []
11: for ln in open(r'C:\Users\135324\.opencodex\usage.jsonl','r',encoding='utf-8',errors='replace'):
12:     ln = ln.strip()
13:     if not ln: continue
14:     try: recs.append(json.loads(ln))
15:     except Exception: pass
16: 
17: print('=== smallest inputTokens seen per conversation (proxy for fresh-session baseline) ===')
18: byc = defaultdict(list)
19: for r in recs:
20:     c = r.get('conversationId') or ''
21:     if not c: continue
22:     byc[c].append(r)
23: 
24: firsts = []
25: for c, rs in byc.items():
26:     rs.sort(key=lambda r: r['timestamp'])
27:     u0 = (rs[0].get('usage') or {}).get('inputTokens') or 0
28:     t0 = datetime.datetime.fromtimestamp(rs[0]['timestamp']/1000, TZ)
29:     if t0 < datetime.datetime(2026,11,6,0,0, tzinfo=TZ): continue
30:     firsts.append((u0/1000, t0.strftime('%m-%d %H:%M'), c[:12], len(rs), rs[0].get('servedModel')))
31: firsts.sort()
32: print('%-8s %-13s %6s %-14s %8s' % ('first_k','time','reqs','model','conv'))
33: for k, t, c, n, m in firsts[:22]:
34:     print('%-8.0f %-13s %6d %-14s %s' % (k, t, n, m, c))
35: 
36: vals = sorted(x[0] for x in firsts)
37: if vals:
38:     print('\nfresh-session baseline: n=%d min=%.0fk p25=%.0fk median=%.0fk max=%.0fk' % (
39:         len(vals), vals[0], vals[int(len(vals)*0.25)], st.median(vals), vals[-1]))
40: 
41: # 2) request body size vs tokens
42: print('\n=== request body bytes vs tokens ===')
43: cur.execute("""select ts, feedback_log_body from logs
44:  where feedback_log_body like '%pre_compression_bytes%' order by ts""")
45: pairs = []
46: for ts, b in cur.fetchall():
47:     m = re.search(r'pre_compression_bytes=(\d+)', b or '')
48:     if not m: continue
49:     pairs.append((ts, int(m.group(1))))
50: print('rows with pre_compression_bytes =', len(pairs))
51: sz = sorted(p[1] for p in pairs)
52: print('body size: min=%.0fKB p10=%.0fKB median=%.0fKB max=%.0fKB' % (
53:     sz[0]/1024, sz[int(len(sz)*0.1)]/1024, st.median(sz)/1024, sz[-1]/1024))

(End of file - total 53 lines)
</content>
```

**Tool:** `read`

```json
{
  "file_path": "D:\\doc\\dsh_workspace\\_codex_probe31.py"
}
```

**Result**

```
<path>D:\doc\dsh_workspace\_codex_probe31.py</path>
<type>file</type>
<content>
1: import sqlite3, re, datetime, statistics as st
2: from collections import OrderedDict
3: 
4: TZ = datetime.timezone(datetime.timedelta(hours=8))
5: con = sqlite3.connect(r'file:C:\Users\135324\.codex\logs_2.sqlite?mode=ro', uri=True)
6: cur = con.cursor()
7: cur.execute("""select ts, feedback_log_body from logs
8:  where feedback_log_body like '%post sampling token usage%' order by ts""")
9: rows = cur.fetchall()
10: print('rows', len(rows))
11: 
12: pat_sub = re.compile(r'submission.id="([0-9a-f\-]+)"')
13: pat_tok = re.compile(r'total_usage_tokens=(\d+)')
14: pat_th  = re.compile(r'thread_id=([0-9a-f\-]+)')
15: 
16: turns = OrderedDict()
17: for ts, b in rows:
18:     b = b or ''
19:     ms = pat_sub.search(b); mt = pat_tok.search(b); mh = pat_th.search(b)
20:     if not (ms and mt): continue
21:     k = ms.group(1)
22:     g = turns.setdefault(k, dict(th=mh.group(1) if mh else '', ts0=ts, ts1=ts, toks=[]))
23:     g['ts1'] = ts
24:     g['toks'].append(int(mt.group(1)))
25: 
26: items = sorted(turns.items(), key=lambda kv: kv[1]['ts0'])
27: print('turns', len(items))
28: 
29: print('\n=== per-turn: context size at each model request (last 30 turns) ===')
30: print('%-8s %-13s %6s %8s %8s %8s' % ('start','thread','reqs','min_k','max_k','last_k'))
31: for k, g in items[-30:]:
32:     t = datetime.datetime.fromtimestamp(g['ts0'], TZ).strftime('%H:%M:%S')
33:     tk = [x/1000 for x in g['toks']]
34:     print('%-8s %-13s %6d %8.0f %8.0f %8.0f' % (t, g['th'][:12], len(tk), min(tk), max(tk), tk[-1]))
35: 
36: # growth inside a turn (per extra request) and across turns within same thread
37: print('\n=== growth per request inside a turn (median/max) ===')
38: allg = []
39: for k, g in items:
40:     tk = g['toks']
41:     for a, b2 in zip(tk, tk[1:]):
42:         allg.append((b2-a)/1000)
43: allg.sort()
44: print('n=%d median=%+.1fk mean=%+.1fk p90=%+.1fk max=%+.1fk' % (
45:     len(allg), st.median(allg), sum(allg)/len(allg), allg[int(len(allg)*0.9)-1], max(allg)))
46: 
47: print('\n=== growth across consecutive turns in the SAME thread (a new user turn) ===')
48: byth = {}
49: for k, g in items:
50:     byth.setdefault(g['th'], []).append(g)
51: cross = []
52: for th, gs in byth.items():
53:     gs.sort(key=lambda g: g['ts0'])
54:     for p, q in zip(gs, gs[1:]):
55:         gap = q['ts0'] - p['ts0']
56:         if gap > 3600: continue
57:         cross.append((q['toks'][0] - p['toks'][-1])/1000)
58: cross.sort()
59: if cross:
60:     print('n=%d median=%+.1fk mean=%+.1fk p90=%+.1fk max=%+.1fk min=%+.1fk' % (
61:         len(cross), st.median(cross), sum(cross)/len(cross),
62:         cross[int(len(cross)*0.9)-1], max(cross), min(cross)))

(End of file - total 62 lines)
</content>
```

**Tool:** `grep`

```json
{
  "pattern": "(?i)redirect_uri|oauth",
  "path": "D:\\doc\\dsh_workspace"
}
```

**Result**

```
Found 1 match

codex_probe.mjs
Line 23: await probe('me-noauth', 'https://chatgpt.com/backend-api/me', {});
```

**Tool:** `pwsh`

```json
{
  "command": "Get-ChildItem -Force D:\\doc\\dsh_workspace\\.tmp_sessions | Select-Object LastWriteTime,Length,Name | Sort-Object LastWriteTime -Descending | Select-Object -First 15 | Format-Table -AutoSize",
  "description": "List recent temp session files"
}
```

**Result**

```

LastWriteTime       Length Name                                              
-------------       ------ ----                                              
2026-11-06 20:16:26    965 win3.cjs                                          
2026-11-06 20:16:16    994 win2.cjs                                          
2026-11-06 20:16:11    676 win.cjs                                           
2026-11-06 20:15:18    735 retry.cjs                                         
2026-11-06 20:14:54   1955 agg.cjs                                           
2026-11-06 20:14:00    550 dbg.cjs                                           
2026-11-06 20:13:51      0 session-e6b1f097-44b4-4cf5-958e-2762e99f0c6f.jsonl
2026-11-06 20:13:51      0 session-59f12f82-5694-4b78-9589-e739eea3b6ef.jsonl
2026-11-06 20:13:50      0 session-2248893f-de8c-412b-851e-37ed68450431.jsonl
2026-11-06 20:13:50  18692 session-f3fb7b97-074f-4937-bf55-296e9a37aeef.jsonl
2026-11-06 20:13:49    654 unz.cjs                                           


```

**Assistant**

这是 **Ory Hydra**（OAuth2 授权服务器）返回的错误页，不是你正在登录的那个应用报的。核心含义一句话：客户端用 `client_id` 发起授权时带的 `redirect_uri`，和该客户端在 Hydra 里**预先登记的地址不是逐字符一致**，所以 Hydra 直接拒绝，连登录页都不给。

## 常见原因（按出现频率）


| #   | 原因         | 例子                                                                                          |
| --- | ---------- | ------------------------------------------------------------------------------------------- |
| 1   | 协议/主机不匹配   | 客户端传 `http://127.0.0.1:1455/...`，登记的是 `http://localhost:1455/...`（这两个在 OAuth 里是**不同的 URI**） |
| 2   | 端口不一致      | 本地回调端口随机或被占用后自动换端口，而登记的是固定端口                                                                |
| 3   | 路径或末尾斜杠差异  | `/auth/callback` vs `/auth/callback/`、`/callback` vs `/oauth/callback`                      |
| 4   | 编码/代理改写    | 回调地址被反向代理、URL 重写或二次 URL 编码（`%3A` 变成 `%253A`）                                                |
| 5   | 客户端配置来源不一致 | 客户端从环境变量/配置文件读到的是另一套回调地址（比如切了环境但没改 `OAUTH_REDIRECT_URI`）                                    |


> 补充：错误文案里那句 "configuration key urls.error is not set" 只是 Hydra 没配置自定义错误页模板，属于噪音，不影响定位。

## 定位方法

从浏览器**地址栏里那条出错的 authorize 请求 URL** 里读出两个值，然后和 Hydra 的登记信息对比：

```
http://<hydra>/oauth2/auth?client_id=XXX&redirect_uri=YYY&response_type=code&scope=...
```

```bash
# 查该客户端登记了哪些回调（需要 admin API 权限）
hydra clients get <client_id> --endpoint http://<hydra-admin>:4445
```

对比 `redirect_uris` 数组里有没有**和 YYY 完全一样**的一项。

## 两种修法

- **改服务端（你是 Hydra 管理员时）**：把出错的那个 URI 原样登记进去
  ```bash
  hydra clients update <client_id> --endpoint http://<hydra-admin>:4445 \
    --redirect-uris http://127.0.0.1:1455/auth/callback
  ```
- **改客户端**：让客户端发送已登记的那个地址（改配置/环境变量/启动参数），不要指望服务端兼容 `localhost` 与 `127.0.0.1`、带不带斜杠这类差异。

要给你精确的修法，我需要知道这次是谁在发起登录：

**Tool:** `ask_user_question`

```json
{
  "questions": [
    {
      "id": "client",
      "header": "确认场景",
      "question": "这次 OAuth 登录是哪个客户端/系统发起的？",
      "options": [
        {
          "label": "codex / opencodex CLI 登录",
          "description": "本地 CLI 走 loopback 回调（常见 1455 端口），多为端口或 localhost/127.0.0.1 不一致"
        },
        {
          "label": "公司内部系统 / SSO",
          "description": "内部网关 OAuth，通常是应用登记的回调地址没同步"
        },
        {
          "label": "我自己搭的 Hydra 服务端",
          "description": "可以改 hydra clients 登记，直接修配"
        },
        {
          "label": "不确定，我只是点了登录就报错",
          "description": "我帮你从浏览器地址栏的 authorize URL 反推"
        }
      ]
    }
  ]
}
```

**Result**

```
{"answers":[{"id":"client","selected":[],"custom":"本机的代理软件 wild-work"}]}
```

**Tool:** `pwsh`

```json
{
  "command": "Get-ChildItem -Force 'D:\\Program Files\\wind-work' | Select-Object Mode,LastWriteTime,Length,Name | Format-Table -AutoSize",
  "description": "List wind-work install directory"
}
```

**Result**

```

Mode   LastWriteTime       Length   Name                           
----   -------------       ------   ----                           
d----- 2026-11-07 13:00:01          auths                          
d----- 2026-11-06 16:50:00          bak                            
d----- 2026-11-07 13:20:08          data                           
-a---- 2026-11-07 13:01:00 3274     config.json                    
-a---- 2026-10-28 16:43:58 2562     config.json.bak-20261028-182521
-a---- 2026-10-28 18:27:39 3370     config.json.bak-20261028-183459
-a---- 2026-10-28 18:35:04 3420     config.json.bak-20261028-184113
-a---- 2026-11-07 0:10:22  20807168 wild-work-windows-amd64.exe    


```

**Tool:** `pwsh`

```json
{
  "command": "Get-ChildItem -Force 'D:\\Program Files\\wind-work' -Recurse -Depth 2 -File -ErrorAction SilentlyContinue | Where-Object { $_.Extension -in '.json','.yaml','.yml','.toml','.ini','.conf','.env' } | Select-Object -First 40 FullName,Length | Format-Table -AutoSize",
  "description": "Find config files in wind-work"
}
```

**Result**

```

FullName                                                                               Length
--------                                                                               ------
D:\Program Files\wind-work\config.json                                                   3274
D:\Program Files\wind-work\auths\loomy-261107125440814968.json                            465
D:\Program Files\wind-work\auths\qodercn-019ed4b3-130d-7d84-9450-c9a0ddcef286.json        618
D:\Program Files\wind-work\auths\qodercom-019cb1b0-0beb-7004-b0d0-f4cbe83191aa.json       613
D:\Program Files\wind-work\auths\raccoon-pu-01a16662-bc55-739e-af97-cfd5a80a2fed.json    1372
D:\Program Files\wind-work\auths\trae-332504448894171.json                               1590
D:\Program Files\wind-work\auths\workbuddy-f9e3fcac-696d-493c-acc2-a62658829377.json     3471
D:\Program Files\wind-work\auths\workbuddyai-ec8e2edd-4b02-472a-90fd-b3955a43535a.json   2259
D:\Program Files\wind-work\data\login-state.json                                          556
D:\Program Files\wind-work\data\pricing-cache.json                                      15853
D:\Program Files\wind-work\data\state-codearts.json                                        36
D:\Program Files\wind-work\data\state-glm.json                                             36
D:\Program Files\wind-work\data\state-kilo.json                                           250
D:\Program Files\wind-work\data\state-lobsterai.json                                       36
D:\Program Files\wind-work\data\state-loomy.json                                          361
D:\Program Files\wind-work\data\state-oczen.json                                          251
D:\Program Files\wind-work\data\state-qodercn.json                                        366
D:\Program Files\wind-work\data\state-qodercom.json                                       608
D:\Program Files\wind-work\data\state-qwenwork.json                                        36
D:\Program Files\wind-work\data\state-raccoon.json                                        404
D:\Program Files\wind-work\data\state-traework.json                                       374
D:\Program Files\wind-work\data\state-workbuddy.json                                      429
D:\Program Files\wind-work\data\state-workbuddyai.json                                    311
D:\Program Files\wind-work\data\state-zcode.json                                           36
D:\Program Files\wind-work\data\stats.json                                              32428
D:\Program Files\wind-work\data\blocked\blocked-1793857255324455100.json               549183
D:\Program Files\wind-work\data\blocked\blocked-1793857704389406000.json               602178
D:\Program Files\wind-work\data\blocked\blocked-1793970785961559000.json               170012
D:\Program Files\wind-work\data\ledger\credit-snapshot.json                              9560


```

**Tool:** `read`

```json
{
  "file_path": "D:\\Program Files\\wind-work\\config.json"
}
```

**Result**

```
<path>D:\Program Files\wind-work\config.json</path>
<type>file</type>
<content>
1: {
2:   "listen": {
3:     "host": "127.0.0.1",
4:     "port": 7863
5:   },
6:   "api_key": "WildWorkAPI",
7:   "admin_password": "",
8:   "auth_dir": "./auths",
9:   "state_file": "./data/state.json",
10:   "region": "cn",
11:   "cooldown": {
12:     "hard_credit": "12h",
13:     "soft_rate": "60s",
14:     "err_threshold": 3,
15:     "err_cooldown": "10m",
16:     "daily_grant_at": "00:00",
17:     "daily_grant_buffer": "30m"
18:   },
19:   "schedule": {
20:     "checkin_hours": [
21:       9,
22:       21
23:     ],
24:     "checkin_times": [
25:       "09:26",
26:       "10:00"
27:     ],
28:     "keepalive_hours": [
29:       22
30:     ],
31:     "expiring_days": 1
32:   },
33:   "upstream": {
34:     "timeout_seconds": 120
35:   },
36:   "server": {
37:     "sticky_max_requests": 50
38:   },
39:   "login": {},
40:   "compat": {
41:     "default_channel": "workbuddy",
42:     "model_map": {},
43:     "max_tokens_cap": 32000
44:   },
45:   "model_fallback": [
46:     {
47:       "from": "traecode/deepseek-v4.1-flash",
48:       "to": [
49:         "raccoon/sn-deepseek-v4-1-flash-1017",
50:         "qodercn/deepseek-flash",
51:         "workbuddyai/deepseek-v4.1-flash-sg",
52:         "workbuddy/deepseek-v4.1-flash",
53:         "loomy/DeepSeek-V4.1-Flash"
54:       ],
55:       "name": "ds-flash"
56:     },
57:     {
58:       "from": "qodercn/deepseek-v4-pro",
59:       "to": [
60:         "workbuddy/deepseek-v4-pro"
61:       ],
62:       "name": "ds-pro"
63:     },
64:     {
65:       "from": "qodercn/glm-5.3",
66:       "to": [
67:         "workbuddyai/glm-5.3",
68:         "workbuddy/glm-5.3"
69:       ],
70:       "name": "glm53"
71:     },
72:     {
73:       "from": "qodercn/kimi-k3.1-pro",
74:       "to": [
75:         "workbuddy/kimi-k3.1-pro"
76:       ],
77:       "name": "k3.1-pro"
78:     },
79:     {
80:       "from": "raccoon/sn-kimi-k3",
81:       "to": [
82:         "traecode/kimi-k3",
83:         "traecode/kimi-k3-auto",
84:         "workbuddyai/kimi-k3",
85:         "workbuddy/kimi-k3-1"
86:       ],
87:       "name": "k3"
88:     },
89:     {
90:       "from": "qodercn/qwen3.8-flash",
91:       "to": [
92:         "qodercom/qwen3.8-flash",
93:         "traework/qwen3.8-flash",
94:         "traecode/qwen3.8-flash",
95:         "loomy/qwen3.8-flash"
96:       ],
97:       "name": "qw-3.8-flash"
98:     },
99:     {
100:       "from": "traecode/glm-5.3-flash",
101:       "to": [
102:         "raccoon/sn-glm-5-3-flash",
103:         "qodercn/glm-5.3-flash",
104:         "workbuddyai/glm-5.3-flash",
105:         "workbuddy/glm-5.3-flash",
106:         "loomy/GLM-5.3-Flash"
107:       ],
108:       "name": "glm53-flash"
109:     }
110:   ],
111:   "reasoning_efforts": {
112:     "ds-flash": "max",
113:     "ds-pro": "high",
114:     "glm53": "max",
115:     "k3": "medium",
116:     "k3.1-pro": "max",
117:     "qodercn/deepseek-flash": "max",
118:     "qodercn/deepseek-v4-pro": "max",
119:     "qodercn/glm-5.3": "max",
120:     "qodercn/glm-5.3-flash": "max",
121:     "qodercn/kimi-k3.1-pro": "max",
122:     "qodercn/qwen3.8-flash": "xhigh",
123:     "qodercom/deepseek-flash": "max",
124:     "qodercom/qwen3.8-flash": "xhigh",
125:     "qw-3.8-flash": "xhigh",
126:     "raccoon/sn-deepseek-v4-1-flash-1017": "max",
127:     "raccoon/sn-glm-5-3": "max",
128:     "raccoon/sn-kimi-k3": "max",
129:     "workbuddy/deepseek-v4-pro": "high",
130:     "workbuddy/deepseek-v4.1-flash": "max",
131:     "workbuddy/glm-5.3": "max",
132:     "workbuddy/glm-5.3-flash": "max",
133:     "workbuddy/kimi-k3-1": "medium",
134:     "workbuddy/kimi-k3.1-pro": "max",
135:     "workbuddyai/deepseek-v4.1-flash": "max",
136:     "workbuddyai/glm-5.3": "max",
137:     "workbuddyai/glm-5.3-flash": "max",
138:     "workbuddyai/kimi-k3": "medium"
139:   },
140:   "features": {
141:     "loop_guard": true
142:   }
143: }

(End of file - total 143 lines)
</content>
```

**Tool:** `read`

```json
{
  "file_path": "D:\\Program Files\\wind-work\\data\\login-state.json"
}
```

**Result**

```
<path>D:\Program Files\wind-work\data\login-state.json</path>
<type>file</type>
<content>
1: {
2:   "verifier": "wivUjXWNoaNS3VQYL4CkGPDYZ5lJ1wKk-DTmGveGc7cYe7562uehXLctcK3jE-IV",
3:   "redirect_uri": "http://127.0.0.1:65369/callback",
4:   "callback_port": 65369,
5:   "auth_url": "https://qwenwork.cn/oauth2/auth?client_id=qwenwork-desktop-app\u0026code_challenge=bZULz54YNVPIXGry5Jp1V3JSexigcw6IDMAX7mZK1go\u0026code_challenge_method=S256\u0026redirect_uri=http%3A%2F%2F127.0.0.1%3A65369%2Fcallback\u0026response_type=code\u0026scope=openid+profile+email+offline_access+qwen_work\u0026state=9ba07d22-30c2-456c-8678-9ac12a77d3bc",
6:   "created_at": 1794028685
7: }

(End of file - total 7 lines)
</content>
```

**Tool:** `pwsh`

```json
{
  "command": "Get-ChildItem 'D:\\Program Files\\wind-work\\data\\state-*.json' | ForEach-Object { \"=== $($_.Name) ===\"; Get-Content -Raw -Encoding UTF8 $_.FullName }",
  "description": "Dump provider state files"
}
```

**Result**

```
=== state-codearts.json ===
{
  "version": 3,
  "accounts": {}
}
=== state-glm.json ===
{
  "version": 3,
  "accounts": {}
}
=== state-kilo.json ===
{
  "version": 3,
  "accounts": {
    "kilo-anonymous": {
      "credits": 0,
      "disabled": false,
      "until": "0001-01-01T00:00:00Z",
      "last_checkin_at": "0001-01-01T00:00:00Z",
      "session_dead_at": "0001-01-01T00:00:00Z"
    }
  }
}
=== state-lobsterai.json ===
{
  "version": 3,
  "accounts": {}
}
=== state-loomy.json ===
{
  "version": 3,
  "accounts": {
    "261107125440814968": {
      "credits": 5379,
      "disabled": false,
      "until": "0001-01-01T00:00:00Z",
      "last_checkin_ok": true,
      "last_checkin_at": "2026-11-07T12:55:18.1506347+08:00",
      "last_checkin_msg": "宠物打工奖励 +300 积分",
      "session_dead_at": "0001-01-01T00:00:00Z"
    }
  }
}
=== state-oczen.json ===
{
  "version": 3,
  "accounts": {
    "oczen-anonymous": {
      "credits": 0,
      "disabled": false,
      "until": "0001-01-01T00:00:00Z",
      "last_checkin_at": "0001-01-01T00:00:00Z",
      "session_dead_at": "0001-01-01T00:00:00Z"
    }
  }
}
=== state-qodercn.json ===
{
  "version": 3,
  "accounts": {
    "019ed4b3-130d-7d84-9450-c9a0ddcef286": {
      "credits": 1913,
      "disabled": false,
      "until": "0001-01-01T00:00:00Z",
      "last_checkin_ok": true,
      "last_checkin_at": "2026-11-07T10:00:02.2287605+08:00",
      "last_checkin_msg": "签到成功 +100",
      "session_dead_at": "0001-01-01T00:00:00Z"
    }
  }
}
=== state-qodercom.json ===
{
  "version": 3,
  "accounts": {
    "019cb1b0-0beb-7004-b0d0-f4cbe83191aa": {
      "credits": 0,
      "disabled": false,
      "until": "0001-01-01T00:00:00Z",
      "last_checkin_at": "2026-11-07T12:00:00.4357889+08:00",
      "last_checkin_msg": "该账号无积分领取活动资格：上游本次没有下发任何领积分活动（showCampaign=true, claimable=true；1 条活动：VIEW_DETAILS=CLAIMABLE；本机时间 11-07 12:00）。同一账号在官方客户端里也看不到该入口 ⇒ 不是本工具的问题，重试无意义",
      "session_dead_at": "0001-01-01T00:00:00Z"
    }
  }
}
=== state-qwenwork.json ===
{
  "version": 3,
  "accounts": {}
}
=== state-raccoon.json ===
{
  "version": 3,
  "accounts": {
    "pu-01a16662-bc55-739e-af97-cfd5a80a2fed": {
      "credits": 8939,
      "earliest_expire": 1794585599,
      "disabled": false,
      "until": "0001-01-01T00:00:00Z",
      "last_checkin_ok": true,
      "last_checkin_at": "2026-11-07T10:00:00.7031868+08:00",
      "last_checkin_msg": "今日已领取",
      "session_dead_at": "0001-01-01T00:00:00Z"
    }
  }
}
=== state-traework.json ===
{
  "version": 3,
  "accounts": {
    "332504448894171": {
      "credits": 3282,
      "earliest_expire": 1794360361,
      "disabled": false,
      "until": "0001-01-01T00:00:00Z",
      "last_checkin_ok": true,
      "last_checkin_at": "2026-11-07T10:00:00.3581662+08:00",
      "last_checkin_msg": "已签到",
      "session_dead_at": "0001-01-01T00:00:00Z"
    }
  }
}
=== state-workbuddy.json ===
{
  "version": 3,
  "accounts": {
    "f9e3fcac-696d-493c-acc2-a62658829377": {
      "credits": 5148,
      "earliest_expire": 1794274450,
      "disabled": false,
      "until": "0001-01-01T00:00:00Z",
      "last_checkin_ok": true,
      "last_checkin_at": "2026-11-07T10:00:00.6634556+08:00",
      "last_checkin_msg": "已签到（连续 37 天，本周 6 天）",
      "session_dead_at": "0001-01-01T00:00:00Z"
    }
  }
}
=== state-workbuddyai.json ===
{
  "version": 3,
  "accounts": {
    "ec8e2edd-4b02-472a-90fd-b3955a43535a": {
      "credits": 811,
      "earliest_expire": 1794781569,
      "disabled": false,
      "until": "0001-01-01T00:00:00Z",
      "last_checkin_at": "0001-01-01T00:00:00Z",
      "session_dead_at": "0001-01-01T00:00:00Z"
    }
  }
}
=== state-zcode.json ===
{
  "version": 3,
  "accounts": {}
}
```

**Tool:** `pwsh`

```json
{
  "command": "$b='D:\\Program Files\\wind-work\\wild-work-windows-amd64.exe'; $s=Select-String -Path $b -Pattern 'callback_port|redirect_uri|127\\.0\\.0\\.1:|login\\.' -AllMatches -Encoding Default -ErrorAction SilentlyContinue; if($s){ $s | Select-Object -First 5 | ForEach-Object { $_.Line.Substring(0,[Math]::Min(300,$_.Line.Length)) } } else { 'no match via Select-String' }",
  "description": "Grep binary for callback port strings"
}
```

**Result**

```
*login.Result
```
