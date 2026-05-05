(() => {
  const hamburger = document.getElementById('hamburger');
  const mobileNav = document.getElementById('mobileNav');
  const closeMenu = () => { if (!hamburger || !mobileNav) return; hamburger.classList.remove('open'); mobileNav.classList.remove('open'); hamburger.setAttribute('aria-expanded','false'); hamburger.setAttribute('aria-label','メニューを開く'); };
  if (hamburger && mobileNav) {
    hamburger.addEventListener('click', () => { const open = !mobileNav.classList.contains('open'); hamburger.classList.toggle('open', open); mobileNav.classList.toggle('open', open); hamburger.setAttribute('aria-expanded', String(open)); hamburger.setAttribute('aria-label', open ? 'メニューを閉じる' : 'メニューを開く'); });
    mobileNav.querySelectorAll('[data-mclose]').forEach(a => a.addEventListener('click', closeMenu));
    document.addEventListener('keydown', e => { if (e.key === 'Escape') closeMenu(); });
  }

  const reveals = document.querySelectorAll('.reveal');
  if ('IntersectionObserver' in window) {
    const io = new IntersectionObserver(entries => entries.forEach(entry => { if (entry.isIntersecting) { entry.target.classList.add('visible'); io.unobserve(entry.target); } }), { threshold: 0.12 });
    reveals.forEach(el => io.observe(el));
  } else { reveals.forEach(el => el.classList.add('visible')); }

  const slideRoot = document.getElementById('heroSlide');
  if (slideRoot) {
    const slides = Array.from(slideRoot.querySelectorAll('.slide'));
    const dots = Array.from(slideRoot.querySelectorAll('.slide-dot'));
    const prev = slideRoot.querySelector('.slide-prev');
    const next = slideRoot.querySelector('.slide-next');
    const pause = document.getElementById('slidePause');
    let index = 0, timer = null, paused = false;
    const show = i => { index = (i + slides.length) % slides.length; slides.forEach((s,n) => s.classList.toggle('active', n === index)); dots.forEach((d,n) => { d.classList.toggle('active', n === index); d.setAttribute('aria-selected', String(n === index)); }); };
    const stop = () => { if (timer) window.clearInterval(timer); timer = null; };
    const start = () => { stop(); if (!paused && slides.length > 1) timer = window.setInterval(() => show(index + 1), 5500); };
    prev?.addEventListener('click', () => { show(index - 1); start(); });
    next?.addEventListener('click', () => { show(index + 1); start(); });
    dots.forEach((d,n) => d.addEventListener('click', () => { show(n); start(); }));
    pause?.addEventListener('click', () => { paused = !paused; pause.setAttribute('aria-label', paused ? '自動再生を再開' : '自動再生を一時停止'); pause.textContent = paused ? '▶' : 'Ⅱ'; paused ? stop() : start(); });
    document.addEventListener('visibilitychange', () => { document.hidden ? stop() : start(); });
    start();
  }

  const toTop = document.getElementById('toTop');
  if (toTop) {
    const toggle = () => toTop.classList.toggle('visible', window.scrollY > 600);
    window.addEventListener('scroll', toggle, { passive: true });
    toggle();
    toTop.addEventListener('click', () => window.scrollTo({ top: 0, behavior: 'smooth' }));
  }

  const trackTel = (href) => { if (typeof gtag === 'function') gtag('event', 'click_tel', { event_category: 'engagement', event_label: href || 'tel' }); };
  document.querySelectorAll('a[href^="tel:"]').forEach(a => a.addEventListener('click', () => trackTel(a.getAttribute('href'))));

  const form = document.getElementById('contactForm');
  if (form) {
    const status = document.getElementById('formStatus');
    const required = Array.from(form.querySelectorAll('[required]'));
    const mark = (el) => { if (el.type !== 'checkbox') el.setAttribute('aria-invalid', String(!el.checkValidity())); };
    required.forEach(el => el.addEventListener('blur', () => mark(el)));
    form.addEventListener('submit', async (e) => {
      e.preventDefault();
      required.forEach(mark);
      if (!form.checkValidity()) { status.textContent = '必須項目をご確認ください。'; status.classList.add('error'); form.reportValidity(); return; }
      const btn = form.querySelector('.form-submit');
      btn.disabled = true; status.textContent = '送信中です。'; status.classList.remove('error');
      try {
        const res = await fetch(form.action, { method: 'POST', body: new FormData(form), headers: { 'Accept': 'application/json' } });
        if (!res.ok) throw new Error('send failed');
        status.textContent = '送信しました。内容を確認のうえ、折り返しご連絡します。';
        form.reset();
        if (typeof gtag === 'function') gtag('event', 'generate_lead', { event_category: 'contact', event_label: 'contact_form' });
      } catch (_) {
        status.textContent = '送信できませんでした。時間をおいて再度お試しいただくか、お電話でご連絡ください。';
        status.classList.add('error');
      } finally { btn.disabled = false; }
    });
  }
})();