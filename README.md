import React from 'react';
import { PRODUCTS, FAQ_LIST, BRAND_NAME, REGION, OWNER_NAME, PHONE } from './constants';
import { AIConsultant } from './components/AIConsultant';
import { Calculator } from './components/Calculator';
import { Quiz } from './components/Quiz';
import { Emblem } from './components/Emblem';

const App: React.FC = () => {
  return (
    <div className="min-h-screen flex flex-col selection:bg-emerald-200 bg-[#FDFBF7] overflow-x-hidden">
      {/* Navigation */}
      <nav className="sticky top-0 z-50 bg-white/95 backdrop-blur-md border-b border-slate-100 px-3 md:px-6 py-2 md:py-4">
        <div className="max-w-7xl mx-auto flex items-center justify-between gap-2">
          <div className="flex items-center gap-2">
            <Emblem size={32} className="md:w-[48px] md:h-[48px] shrink-0" />
            <div className="min-w-0">
              <h1 className="text-[12px] md:text-xl font-black text-slate-900 leading-none truncate">{BRAND_NAME}</h1>
              <p className="text-[7px] md:text-[10px] text-emerald-600 font-bold uppercase tracking-widest mt-0.5 truncate">{REGION}</p>
            </div>
          </div>
          <div className="flex items-center shrink-0">
            <a 
              href={`tel:${PHONE.replace(/\D/g, '')}`}
              className="bg-emerald-600 text-white px-3 md:px-6 py-2 md:py-3 rounded-lg md:rounded-2xl text-[10px] md:text-sm font-black shadow-lg shadow-emerald-600/20 whitespace-nowrap"
            >
              {PHONE}
            </a>
          </div>
        </div>
      </nav>

      {/* Hero Section */}
      <header className="relative pt-12 md:pt-24 pb-16 md:pb-40 px-4 md:px-6 overflow-hidden flex flex-col items-center justify-center text-center">
        <div className="max-w-4xl mx-auto opacity-0 animate-reveal">
          <div className="inline-flex items-center gap-2 px-3 py-1 bg-emerald-100 text-emerald-800 rounded-full text-[9px] md:text-xs font-black uppercase tracking-widest mb-6 md:mb-8">
            <span>🌿 Натуральное хозяйство</span>
            <span className="w-1 h-1 bg-emerald-300 rounded-full"></span>
            <span>🚚 Доставка до двери</span>
          </div>
          <h2 className="text-4xl md:text-8xl font-black text-slate-900 leading-[1.1] mb-6 md:mb-10 tracking-tighter">
            Домашняя индейка <br/><span className="text-emerald-600 italic">с заботой</span>
          </h2>
          <p className="text-base md:text-2xl text-slate-600 mb-8 md:mb-14 max-w-2xl mx-auto leading-relaxed">
            Мясо, яйца и индюшата из первых рук. Мы выращиваем птицу на натуральных кормах и сами привозим её к вашему порогу.
          </p>
          <div className="flex flex-col sm:flex-row gap-4 md:gap-6 justify-center">
            <button 
              onClick={() => document.getElementById('products')?.scrollIntoView({ behavior: 'smooth' })}
              className="bg-emerald-700 text-white px-8 md:px-14 py-4 md:py-6 rounded-xl md:rounded-[2.5rem] font-black text-lg md:text-xl shadow-xl hover:bg-emerald-800 hover:-translate-y-1 transition-all active:scale-95"
            >
              Посмотреть продукцию
            </button>
            <button 
              onClick={() => document.getElementById('delivery')?.scrollIntoView({ behavior: 'smooth' })}
              className="bg-white text-emerald-900 border-2 border-emerald-50 px-8 md:px-14 py-4 md:py-6 rounded-xl md:rounded-[2.5rem] font-black text-lg md:text-xl shadow-lg hover:bg-emerald-50 hover:-translate-y-1 transition-all active:scale-95"
            >
              Условия доставки
            </button>
          </div>
        </div>
      </header>

      {/* Trust Factors */}
      <section className="py-12 md:py-24 bg-white px-4">
        <div className="max-w-7xl mx-auto">
          <div className="grid grid-cols-2 lg:grid-cols-4 gap-4 md:gap-12">
            {[
              { t: 'Своё зерно', i: '🌾' },
              { t: 'Свежий забой', i: '🗡️' },
              { t: 'Живая связь', i: '📱' },
              { t: 'Честный вес', i: '⚖️' }
            ].map((f, idx) => (
              <div key={idx} className="bg-slate-50 p-4 md:p-10 rounded-2xl md:rounded-[2.5rem] text-center">
                <div className="text-3xl md:text-5xl mb-2 md:mb-6">{f.i}</div>
                <h4 className="text-[11px] md:text-xl font-black text-slate-900 leading-tight">{f.t}</h4>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Products Section */}
      <section id="products" className="py-12 md:py-32 bg-slate-50 px-4">
        <div className="max-w-7xl mx-auto">
          <h2 className="text-2xl md:text-6xl font-black text-slate-900 mb-8 leading-tight">Наша продукция</h2>
          <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-8">
            {PRODUCTS.map((p) => (
              <div key={p.id} className="bg-white p-5 md:p-10 rounded-2xl md:rounded-[3rem] shadow-sm border border-slate-100 flex flex-col">
                <div className="text-4xl md:text-6xl mb-4 md:mb-8">{p.icon}</div>
                <h3 className="text-lg md:text-2xl font-black text-slate-900 mb-2">{p.title}</h3>
                <p className="text-slate-500 text-[11px] md:text-sm mb-6 leading-relaxed flex-1 italic">"{p.description}"</p>
                <div className="pt-4 border-t border-slate-50 flex items-center justify-between">
                  <div>
                    <span className="text-slate-400 text-[8px] md:text-[10px] font-black uppercase block">{p.unit}</span>
                    <span className="text-xl md:text-3xl font-black text-emerald-800">{p.price} ₽</span>
                  </div>
                  <button 
                    onClick={() => document.getElementById('calc')?.scrollIntoView({ behavior: 'smooth' })}
                    className="w-10 h-10 md:w-14 md:h-14 bg-emerald-600 text-white rounded-xl flex items-center justify-center font-bold"
                  >
                    +
                  </button>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Delivery Section */}
      <section id="delivery" className="py-16 md:py-32 bg-emerald-900 text-white px-4">
        <div className="max-w-7xl mx-auto">
          <div className="text-center mb-12 md:mb-20">
            <h2 className="text-3xl md:text-6xl font-black mb-6">Доставим свежее <br/><span className="text-emerald-400">к вашему столу</span></h2>
            <p className="text-emerald-100/70 text-base md:text-xl max-w-2xl mx-auto">Бережно упаковываем продукцию и привозим в удобное для вас время. Мы гарантируем свежесть каждого заказа.</p>
          </div>
          
          <div className="grid grid-cols-1 md:grid-cols-3 gap-6 md:gap-10 mb-16">
            <div className="bg-white/5 border border-white/10 p-8 rounded-[2rem] md:rounded-[3rem] flex flex-col items-center text-center">
              <div className="text-5xl mb-6">🏘️</div>
              <h3 className="text-xl md:text-2xl font-black mb-4">Самовывоз</h3>
              <p className="text-emerald-100/60 text-sm md:text-base leading-relaxed">
                Забирайте заказ прямо с фермы в Куликовке. Заодно сможете посмотреть, как мы содержим птицу.
              </p>
              <div className="mt-6 pt-6 border-t border-white/10 w-full text-emerald-400 font-bold">
                Бесплатно
              </div>
            </div>

            <div className="bg-white/10 border border-emerald-400/30 p-8 rounded-[2rem] md:rounded-[3rem] flex flex-col items-center text-center relative overflow-hidden">
              <div className="absolute top-4 right-6 bg-emerald-500 text-emerald-950 text-[10px] font-black px-3 py-1 rounded-full uppercase">Популярно</div>
              <div className="text-5xl mb-6">🏙️</div>
              <h3 className="text-xl md:text-2xl font-black mb-4">Димитровград</h3>
              <p className="text-emerald-100/60 text-sm md:text-base leading-relaxed">
                Регулярные рейсы в город. Доставляем до подъезда или калитки. Привозим мясо в день забоя.
              </p>
              <div className="mt-6 pt-6 border-t border-white/10 w-full text-emerald-400 font-bold">
                Цена — 500 ₽
              </div>
            </div>

            <div className="bg-white/5 border border-white/10 p-8 rounded-[2rem] md:rounded-[3rem] flex flex-col items-center text-center">
              <div className="text-5xl mb-6">🚜</div>
              <h3 className="text-xl md:text-2xl font-black mb-4">По району</h3>
              <p className="text-emerald-100/60 text-sm md:text-base leading-relaxed">
                Мулловка, Лесной, Новая Майна и другие села. Собираем коллективные заявки для выгодной доставки.
              </p>
              <div className="mt-6 pt-6 border-t border-white/10 w-full text-emerald-400 font-bold">
                По договоренности
              </div>
            </div>
          </div>

          <div className="bg-emerald-800/50 rounded-[2rem] md:rounded-[3rem] p-6 md:p-12 border border-emerald-700 flex flex-col md:flex-row items-center gap-8 md:gap-12">
            <div className="w-20 h-20 md:w-24 md:h-24 bg-emerald-600 rounded-full flex items-center justify-center text-4xl shrink-0">📅</div>
            <div>
              <h4 className="text-xl md:text-3xl font-black mb-2">График доставки</h4>
              <p className="text-emerald-100/70 text-sm md:text-lg">Мы формируем заказы в течение недели и развозим их по выходным или в праздничные дни. Забой индейки производим за 12-24 часа до выезда к вам, чтобы мясо было максимально свежим.</p>
            </div>
          </div>
        </div>
      </section>

      {/* Calculator Section */}
      <section id="calc" className="py-12 md:py-32 px-4 bg-white">
        <div className="max-w-5xl mx-auto">
          <Calculator />
        </div>
      </section>

      {/* Quiz Section */}
      <section id="quiz" className="py-12 md:py-32 px-4 bg-[#FDFBF7]">
        <div className="max-w-3xl mx-auto">
          <Quiz />
        </div>
      </section>

      {/* Farmer Section */}
      <section id="about" className="py-16 md:py-32 bg-white">
        <div className="max-w-7xl mx-auto px-6 grid lg:grid-cols-5 gap-12 md:gap-20 items-center">
          <div className="lg:col-span-2">
            <div className="relative bg-emerald-900 rounded-3xl md:rounded-[4rem] p-8 md:p-10 text-emerald-100 shadow-2xl">
              <div className="text-5xl mb-6">👨‍🌾</div>
              <h2 className="text-3xl md:text-4xl font-black text-white mb-4 md:mb-6 leading-tight">Фермер Дмитрий</h2>
              <p className="italic text-base md:text-lg mb-6 md:mb-8 leading-relaxed opacity-90">
                "Я занимаюсь индюками с 2008 года. Моя цель — чтобы на вашем столе был по-настоящему чистый и полезный продукт."
              </p>
              <div className="flex items-center gap-3 md:gap-4 border-t border-white/10 pt-6 md:pt-8">
                <div className="w-10 h-10 md:w-14 md:h-14 bg-white/20 rounded-xl md:rounded-2xl flex items-center justify-center text-lg md:text-xl">🏠</div>
                <div>
                  <p className="font-black text-white text-sm md:text-lg leading-none mb-1">Ферма в Куликовке</p>
                  <p className="text-[8px] md:text-xs font-bold uppercase tracking-widest text-emerald-400">Собственное производство</p>
                </div>
              </div>
            </div>
          </div>
          <div className="lg:col-span-3">
            <h3 className="text-2xl md:text-3xl font-black text-slate-900 mb-6 md:mb-8 leading-tight">Задайте вопрос Дмитрию <br/><span className="text-emerald-600">прямо сейчас</span></h3>
            <AIConsultant />
          </div>
        </div>
      </section>

      {/* FAQ */}
      <section id="faq" className="py-16 md:py-32 bg-slate-50">
        <div className="max-w-4xl mx-auto px-6">
          <h2 className="text-3xl md:text-5xl font-black text-slate-900 mb-10 md:mb-16 text-center">Частые вопросы</h2>
          <div className="space-y-4 md:space-y-8">
            {FAQ_LIST.map((item, idx) => (
              <div key={idx} className="p-6 md:p-10 bg-white rounded-2xl md:rounded-[2.5rem] shadow-sm border border-slate-100 group">
                <h4 className="text-lg md:text-2xl font-black text-slate-900 mb-3 md:mb-4 leading-tight">{item.question}</h4>
                <p className="text-slate-500 text-sm md:text-lg leading-relaxed font-medium">{item.answer}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Footer / Contact */}
      <footer id="order" className="bg-emerald-950 text-white py-12 md:py-32 px-4">
        <div className="max-w-7xl mx-auto">
          <div className="grid lg:grid-cols-2 gap-12 md:gap-24">
            <div>
              <h2 className="text-3xl md:text-6xl font-black mb-8">Контакты</h2>
              <div className="space-y-6 md:space-y-12">
                <div className="flex items-center gap-4 md:gap-8">
                  <div className="w-12 h-12 md:w-20 md:h-20 bg-emerald-800 rounded-xl md:rounded-[2rem] flex items-center justify-center text-xl md:text-4xl">📱</div>
                  <div>
                    <p className="text-emerald-400 font-black uppercase text-[8px] md:text-xs mb-1">Фермер Дмитрий</p>
                    <a href={`tel:${PHONE.replace(/\D/g, '')}`} className="text-lg md:text-3xl font-black">{PHONE}</a>
                  </div>
                </div>
                <div className="flex items-center gap-4 md:gap-8">
                  <div className="w-12 h-12 md:w-20 md:h-20 bg-emerald-800 rounded-xl md:rounded-[2rem] flex items-center justify-center text-xl md:text-4xl">📍</div>
                  <div>
                    <p className="text-emerald-400 font-black uppercase text-[8px] md:text-xs mb-1">Местоположение</p>
                    <p className="text-base md:text-2xl font-black italic">{REGION}</p>
                  </div>
                </div>
              </div>
            </div>
            <form 
              className="bg-white/5 p-6 md:p-12 rounded-2xl md:rounded-[4rem] border border-white/10"
              onSubmit={(e) => { e.preventDefault(); alert(`Заявка принята!`); }}
            >
              <h3 className="text-lg md:text-3xl font-black mb-6 text-emerald-400">Оставить заявку</h3>
              <div className="space-y-4">
                <input type="text" placeholder="Имя" className="w-full bg-white/10 rounded-xl md:rounded-3xl px-5 md:px-8 py-3.5 md:py-5 text-sm md:text-xl text-white outline-none" required />
                <input type="tel" placeholder="Телефон" className="w-full bg-white/10 rounded-xl md:rounded-3xl px-5 md:px-8 py-3.5 md:py-5 text-sm md:text-xl text-white outline-none" required />
                <textarea placeholder="Сообщение" className="w-full bg-white/10 rounded-xl md:rounded-3xl px-5 md:px-8 py-3.5 md:py-5 text-sm md:text-xl text-white h-24 md:h-40 outline-none" required></textarea>
                <button type="submit" className="w-full bg-emerald-500 text-emerald-950 py-4 md:py-6 rounded-xl md:rounded-3xl font-black text-base md:text-2xl active:scale-95 transition-transform">
                  Отправить
                </button>
              </div>
            </form>
          </div>
          <div className="mt-12 pt-8 border-t border-white/5 flex flex-col md:flex-row justify-between items-center gap-4 text-[10px] md:text-sm text-emerald-500/60 font-medium">
            <div className="flex items-center gap-3">
              <Emblem size={24} />
              <span className="font-black text-white uppercase text-xs">{BRAND_NAME}</span>
            </div>
            <p>© 2025. Димитровград.</p>
          </div>
        </div>
      </footer>
    </div>
  );
};

export default App;
