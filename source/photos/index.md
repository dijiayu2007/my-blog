---
title: 我的相册
date: 2026-10-29 18:00:00
layout: page
---

<div class="win7-gallery">
<div class="gallery-item" data-index="0"><img src="https://s41.ax1x.com/2026/10/29/pnycEuQ.jpg" alt="滕王阁"></div>
<div class="gallery-item" data-index="1"><img src="https://s41.ax1x.com/2026/10/29/pnyci38.jpg" alt="香港坚尼地城"></div>
<div class="gallery-item" data-index="2"><img src="https://s41.ax1x.com/2026/10/29/pnyUzW9.jpg" alt="塔斯汀汉堡"></div>
<div class="gallery-item" data-index="3"><img src="https://s41.ax1x.com/2026/10/29/pnycZHs.jpg" alt="香港街景"></div>
<div class="gallery-item" data-index="4"><img src="https://s41.ax1x.com/2026/10/29/pnycmEn.jpg" alt="旺角地铁站"></div>
</div>

<div id="win7-photo-modal" class="window glass active" style="display: none; position: fixed; top: 10%; left: 50%; transform: translateX(-50%); width: 600px; max-width: 90vw; z-index: 99999; padding: 0; border-radius: 8px; overflow: hidden; box-shadow: 0 10px 30px rgba(0,0,0,0.5);">
<div class="title-bar" id="photo-modal-header" style="cursor: move; height: 32px; display: flex; align-items: center; justify-content: space-between; padding: 0 10px; box-sizing: border-box;">
<div class="title-bar-text" id="modal-title" style="font-size: 13px; font-weight: normal; display: flex; align-items: center;">
<img src="/image/icon/vista_photo_gallery.jpg" width="16" height="16" style="margin-right: 5px; width: 16px; height: 16px;" alt=""> 图片查看器
</div>
<div class="title-bar-controls" style="display: flex; align-items: center;">
<button aria-label="Close" id="close-photo-btn" style="cursor: pointer;"></button>
</div>
</div>
<div class="window-body" style="padding: 15px; background: #f0f0f0; margin: 0;">
<div style="background: #111; text-align: center; border: 1px solid #999; display: flex; justify-content: center; align-items: center; height: 400px; max-height: 60vh; overflow: hidden;">
<img id="modal-img" src="" alt="" style="max-width: 100%; max-height: 100%; object-fit: contain; display: block;">
</div>
<div id="modal-info-box" style="margin-top: 15px; display: flex; justify-content: space-between; align-items: flex-end;">
<div id="modal-desc" style="font-size: 14px; color: #333; line-height: 1.5; flex: 1; margin-right: 15px;"></div>
<div id="modal-link-container">
<a id="modal-link" href="#" style="display: inline-block; padding: 6px 15px; text-decoration: none; font-size: 13px; white-space: nowrap;">阅读相关文章 &gt;</a>
</div>
</div>
</div>
</div>

<style>
.win7-gallery { display: grid; grid-template-columns: repeat(5, 1fr); gap: 15px; margin-top: 20px; }
@media (max-width: 1024px) { .win7-gallery { grid-template-columns: repeat(3, 1fr); } }
@media (max-width: 768px) { .win7-gallery { grid-template-columns: repeat(2, 1fr); } }
.gallery-item { cursor: pointer; transition: transform 0.2s, filter 0.2s; background: transparent; padding: 0; border: none; box-shadow: none; }
.gallery-item:hover { transform: translateY(-3px) scale(1.03); filter: brightness(1.1); }
.gallery-item img { width: 100%; aspect-ratio: 1 / 1; object-fit: cover; border-radius: 6px; box-shadow: 0 4px 12px rgba(0,0,0,0.15); border: 1px solid rgba(255,255,255,0.2); }
</style>

<script>
var photoData = [
{ img: 'https://s41.ax1x.com/2026/10/29/pnycEuQ.jpg', title: '滕王阁', desc: '落霞与孤鹜齐飞，秋水共长天一色。', link: '' },
{ img: 'https://s41.ax1x.com/2026/10/29/pnyci38.jpg', title: '香港坚尼地城', desc: '海边街景，自带一种老香港的胶片感。', link: '' },
{ img: 'https://s41.ax1x.com/2026/10/29/pnyUzW9.jpg', title: '塔斯汀pingu联名', desc: '现烤的饼皮真的很有嚼劲，今天这顿没踩雷。', link: '/2026/10/29/tastien/' },
{ img: 'https://s41.ax1x.com/2026/10/29/pnycZHs.jpg', title: '香港街景', desc: '穿梭在密集的招牌和叮叮车之间。', link: '' },
{ img: 'https://s41.ax1x.com/2026/10/29/pnycmEn.jpg', title: '旺角地铁站', desc: '经典的港铁红底白字站标，拍照打卡必备。', link: '' }
];

window.addEventListener('DOMContentLoaded', function() {
var items = document.querySelectorAll('.gallery-item');
items.forEach(function(item) {
item.addEventListener('click', function() {
var index = this.getAttribute('data-index');
var data = photoData[index];
var modalImg = document.getElementById('modal-img');
if(modalImg) modalImg.src = data.img;
var modalTitle = document.getElementById('modal-title');
if(modalTitle) modalTitle.innerHTML = '<img src="/image/icon/vista_photo_gallery.jpg" width="16" height="16" style="margin-right: 5px; width: 16px; height: 16px;" alt=""> ' + data.title;
var descEl = document.getElementById('modal-desc');
if(descEl) {
if (data.desc) { descEl.innerText = data.desc; descEl.style.display = 'block'; } else { descEl.style.display = 'none'; }
}
var linkBox = document.getElementById('modal-link-container');
var linkBtn = document.getElementById('modal-link');
if(linkBox && linkBtn) {
if (data.link) { linkBtn.href = data.link; linkBox.style.display = 'block'; } else { linkBox.style.display = 'none'; }
}
var modal = document.getElementById('win7-photo-modal');
if(modal) modal.style.display = 'block';
});
});
var closeBtn = document.getElementById('close-photo-btn');
if(closeBtn) {
closeBtn.addEventListener('click', function() {
document.getElementById('win7-photo-modal').style.display = 'none';
});
}
var header = document.getElementById('photo-modal-header');
var modal = document.getElementById('win7-photo-modal');
if(header && modal) {
var pos1 = 0, pos2 = 0, pos3 = 0, pos4 = 0;
header.onmousedown = dragMouseDown;
function dragMouseDown(e) {
e = e || window.event; 
if (e.target.getAttribute('aria-label') === 'Close' || e.target.id === 'close-photo-btn') return;
e.preventDefault();
pos3 = e.clientX; pos4 = e.clientY;
document.onmouseup = closeDragElement;
document.onmousemove = elementDrag;
}
function elementDrag(e) {
e = e || window.event; e.preventDefault();
pos1 = pos3 - e.clientX; pos2 = pos4 - e.clientY;
pos3 = e.clientX; pos4 = e.clientY;
modal.style.top = (modal.offsetTop - pos2) + "px";
modal.style.left = (modal.offsetLeft - pos1) + "px";
modal.style.transform = 'none';
modal.style.right = 'auto'; modal.style.bottom = 'auto';
}
function closeDragElement() { document.onmouseup = null; document.onmousemove = null; }
}
});
</script>