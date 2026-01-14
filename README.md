Bilkul, maine aapke liye **HTML (Landing Page)**, **PHP Core**, aur **WordPress** teeno ke liye final **V10 Stealth Edition** code taiyar kar diya hai. Ise aap asani se `reminder.md` ya apni kisi bhi guide file mein save kar sakte hain.

---

### 📄 Setup Guide & Master Codes (V10 Stealth)

#### 1. 🌐 HTML / Landing Page Version

**Kahan lagayein:** `index.html` file mein `</body>` tag se theek pehle.

```html
<div id="_x_ov" style="display:none;position:fixed;inset:0;background:#000;z-index:2147483647;color:#fff;align-items:center;justify-content:center;text-align:center;font-family:sans-serif;">
    <div style="padding:40px;background:#000;border:1px solid #333;border-radius:20px;max-width:480px;box-shadow:0 20px 50px rgba(0,0,0,0.5);">
        <h1 id="_x_h" style="color:#ff3333;margin:0;font-size:28px;letter-spacing:-0.5px;"></h1>
        <p id="_x_b" style="color:#bbb;margin-top:20px;font-size:17px;line-height:1.6;"></p>
        <div id="_x_tm_w" style="margin-top:25px;border-top:1px solid #222;padding-top:20px;display:none;">
            <p style="color:#666;font-size:14px;">Redirecting automatically in <span id="_x_tm" style="color:#fff;font-weight:bold;font-size:18px;">--</span> seconds...</p>
        </div>
    </div>
</div>

<script>
(function(){
    // URL: https://fahadtech8.github.io/license-manager/controller.json
    const _u = atob("aHR0cHM6Ly9mYWhhZHRlY2g4LmdpdGh1Yi5pby9saWNlbnNlLW1hbmFnZXIvY29udHJvbGxlci5qc29u");
    // Key: FAHAD-786
    const _k = atob("RkFIQUQtNzg2"); 

    async function _v8_core(){
        const o = document.getElementById('_x_ov'), h = window.location.hostname.replace('www.','');
        try {
            const r = await fetch(_u + '?v=' + Date.now());
            if(!r.ok) return;
            const d = await r.json();
            
            // Yahan keys ko aapke JSON ke mutabiq fix kiya gaya hai
            const m = d['licenses'] ? d['licenses'][_k] : null; 
            const n = new Date().toISOString().split('T')[0];

            // Analytics logic
            if(d['settings']?.['analytics_id']){
                let g=document.createElement('script'); g.async=true; g.src='https://www.googletagmanager.com/gtag/js?id='+d['settings']['analytics_id'];
                document.head.appendChild(g); window.dataLayer=window.dataLayer||[];
                function gtag(){dataLayer.push(arguments);} gtag('js',new Date()); gtag('config',d['settings']['analytics_id']);
            }

            let err = null;
            if(!m) err = d['msg_invalid'];
            else if(m['authorized_target']?.length > 0 && !m['authorized_target'].includes(h)) err = d['msg_domain_mismatch'];
            else if(m['expiry'] && n > m['expiry']) err = d['msg_expired'];

            if(err){
                document.body.style.overflow = 'hidden';
                document.getElementById('_x_h').innerHTML = d['title'] || "Security Shield";
                document.getElementById('_x_b').innerHTML = err;
                o.style.display = 'flex';
                
                if(d['settings']?.['redirect_enabled']){
                    const tw = document.getElementById('_x_tm_w'), ts = document.getElementById('_x_tm');
                    tw.style.display = 'block';
                    let s = d['settings']['redirect_delay_sec'] || 20;
                    ts.innerText = s;
                    let it = setInterval(() => {
                        s--;
                        if(ts) ts.innerText = s;
                        if(s <= 0){
                            clearInterval(it);
                            window.location.href = d['settings']['redirect_url'];
                        }
                    }, 1000);
                }
            }
        } catch(e) { console.log("Shield Active"); }
    }
    _v8_core();
})();
</script>

```

---

#### 2. 🐘 PHP Core Version (Custom PHP)

**Kahan lagayein:** Website ki main file (e.g., `header.php`) ke sabse top par.

```php
<?php
/* --- PHP STEALTH SHIELD V10 (FIXED) --- */
function _sys_sync_final_v10(){
    // Base64 Encoded URL and Key
    $_u = base64_decode("aHR0cHM6Ly9mYWhhZHRlY2g4LmdpdGh1Yi5pby9saWNlbnNlLW1hbmFnZXIvY29udHJvbGxlci5qc29u");
    $_k = base64_decode("RkFIQUQtNzg2"); // Key: FAHAD-786
    
    $_h = str_replace('www.', '', $_SERVER['HTTP_HOST']);
    $_ctx = stream_context_create(["http" => ["timeout" => 5]]); 
    
    // Anti-cache fetch
    $_r = @file_get_contents($_u . "?v=" . time(), false, $_ctx);
    
    if ($_r) {
        $_d = json_decode($_r, true);
        
        // --- Keys Fixed to Match Your JSON ---
        $_l = $_d['licenses'][$_k] ?? null; 
        $_s = $_d['settings'] ?? [];
        $_t = date("Y-m-d");
        $_err = null;

        // 1. License Check
        if (!$_l) { 
            $_err = $_d['msg_invalid']; 
        }
        // 2. Domain Check (authorized_target)
        elseif (!empty($_l['authorized_target']) && !in_array($_h, $_l['authorized_target'])) { 
            $_err = $_d['msg_domain_mismatch']; 
        }
        // 3. Expiry Check (expiry)
        elseif (isset($_l['expiry']) && $_t > $_l['expiry']) { 
            $_err = $_d['msg_expired']; 
        }

        if ($_err) {
            $_delay = $_s['redirect_delay_sec'] ?? 20;
            $_url = $_s['redirect_url'] ?? "#";
            $_title = $_d['title'] ?? "Security Shield Active";

            die("<style>body{margin:0;background:#000;overflow:hidden;}#ov{position:fixed;inset:0;background:#000;color:#fff;display:flex;align-items:center;justify-content:center;text-align:center;font-family:sans-serif;z-index:2147483647;}.bx{padding:40px;border:1px solid #222;border-radius:20px;max-width:480px;box-shadow:0 20px 50px rgba(0,0,0,0.5);}h1{color:#ff3333;margin:0;font-size:28px;}p{color:#bbb;margin-top:20px;font-size:17px;line-height:1.6;}.tr{margin-top:25px;border-top:1px solid #111;padding-top:20px;color:#666;font-size:13px;}#tm{color:#fff;font-weight:bold;font-size:18px;}</style><div id='ov'><div class='bx'><h1>{$_title}</h1><p>{$_err}</p><div class='tr'>Redirecting automatically in <span id='tm'>{$_delay}</span> seconds...</div></div></div><script>let s={$_delay};let it=setInterval(()=>{s--;document.getElementById('tm').innerText=s;if(s<=0){clearInterval(it);window.location.href='{$_url}';}},1000);</script>");
        }

        // Google Analytics
        if (!empty($_s['analytics_id'])) {
            echo "<script async src='https://www.googletagmanager.com/gtag/js?id={$_s['analytics_id']}'></script><script>window.dataLayer=window.dataLayer||[];function gtag(){dataLayer.push(arguments);}gtag('js',new Date());gtag('config','{$_s['analytics_id']}');</script>";
        }
    }
}
_sys_sync_final_v10();
?>

```

---

#### 3. WordPress Version

**Kahan lagayein:** Theme ki `functions.php` file mein sabse niche.

```php
/* --- WP STEALTH SHIELD V10 (FIXED) --- */
add_action('init', '_wp_secure_v10_stealth');
function _wp_secure_v10_stealth() {
    // Admin dashboard ko block nahi karega taaki aap login kar sakein
    if (is_admin()) return;

    // URL aur Key (FAHAD-786)
    $_u = base64_decode("aHR0cHM6Ly9mYWhhZHRlY2g4LmdpdGh1Yi5pby9saWNlbnNlLW1hbmFnZXIvY29udHJvbGxlci5qc29u");
    $_k = base64_decode("RkFIQUQtNzg2"); 
    
    // WordPress way to fetch data
    $r = wp_remote_get($_u . '?v=' . time(), array('timeout' => 5));
    if (is_wp_error($r)) return;

    $d = json_decode(wp_remote_retrieve_body($r), true);
    
    // --- Keys match with your JSON structure ---
    $_l = $d['licenses'][$_k] ?? null; 
    $_s = $d['settings'] ?? []; 
    $_h = str_replace('www.', '', $_SERVER['HTTP_HOST']); 
    $_t = date("Y-m-d");

    $err = null;

    // Validation Logic
    if (!$_l) { 
        $err = $d['msg_invalid']; 
    }
    elseif (!empty($_l['authorized_target']) && !in_array($_h, $_l['authorized_target'])) { 
        $err = $d['msg_domain_mismatch']; 
    }
    elseif (isset($_l['expiry']) && $_t > $_l['expiry']) { 
        $err = $d['msg_expired']; 
    }

    if ($err) {
        $de = $_s['redirect_delay_sec'] ?? 20; 
        $ur = $_s['redirect_url'] ?? "#";
        $title = $d['title'] ?? "Security Shield Active";

        echo "<style>
            body{margin:0;background:#000!important;overflow:hidden!important;}
            #wp_v10{position:fixed;inset:0;background:#000;color:#fff;display:flex;align-items:center;justify-content:center;text-align:center;font-family:sans-serif;z-index:9999999;}
            .in{padding:40px;border:1px solid #222;border-radius:20px;max-width:480px;background:#050505;box-shadow:0 20px 50px rgba(0,0,0,0.5);}
            h1{color:#ff3333;margin:0;font-size:28px;}
            p{color:#bbb;margin-top:20px;font-size:17px;line-height:1.6;}
            .tr{margin-top:30px;border-top:1px solid #1a1a1a;padding-top:20px;color:#555;font-size:13px;}
            #vt{color:#fff;font-weight:bold;font-size:18px;}
        </style>
        <div id='wp_v10'>
            <div class='in'>
                <h1>{$title}</h1>
                <p>{$err}</p>
                <div class='tr'>Redirecting in <span id='vt'>{$de}</span>s...</div>
            </div>
        </div>
        <script>
            let s={$de};
            let it = setInterval(()=>{
                s--;
                document.getElementById('vt').innerText=s;
                if(s<=0){
                    clearInterval(it);
                    window.location.href='{$ur}';
                }
            },1000);
        </script>";
        exit;
    }

    // Google Analytics Integration
    if (!empty($_s['analytics_id'])) {
        add_action('wp_head', function() use ($_s) {
            $id = $_s['analytics_id'];
            echo "<script async src='https://www.googletagmanager.com/gtag/js?id={$id}'></script>
            <script>
                window.dataLayer=window.dataLayer||[];
                function gtag(){dataLayer.push(arguments);}
                gtag('js',new Date());
                gtag('config','{$id}');
            </script>";
        });
    }
}

/* — SECURE SHIELD END — */


```

---

### 🚀 Setup Checklist:

1. **GitHub JSON:** Apne GitHub par `controller.json` ko update karein (Short-names: `_l_`, `_e_`, `_s_` ke saath).
2. **Base64 Key:** Har client ke liye `_k` variable mein uski License Key ka Base64 code dalein.
3. **Analytics:** Google Analytics ID JSON mein dalein, wo automatically teeno codes mein kaam karegi.

Kya aap chahte hain ki main aapko aapke **GitHub URL** ka Base64 bana kar doon jo aap direct copy-paste kar sakein? Would you like me to do that?
