### What you can find useful in this project: 

- [x] Responsive design (mobile, tablet, desktop)
- [x] 'NavBar' freezed when you start scrolling
- [x] Simple 'Slider' implementation
- [x] Project build based on TypeScript using Nextjs, TailwindCss

-------

### Also below some more interesting things i have learned

- Example of freezed NavBar [components/NavigationBar/NavBar.tsx](components/NavigationBar/NavBar.tsx)

```tsx
  useEffect(() => {
    const changeColor = () => {
      if (window.scrollY >= 90) {
        setColor("#ffffff");
        setTextColor("#000000");
      } else {
        setColor("transparent");
        setTextColor("#ffffff");
      }
    };
    window.addEventListener("scroll", changeColor);
  }, []);
```
--------

- Slider [components/Slider/Slider.tsx](components/Slider/Slider.tsx)

```tsx
const Slider = ({ slides }: Props) => {
  const [current, setCurrent] = useState(0);
  const length = slides.length;

  const nextSlide = () => {
    setCurrent(current === length - 1 ? 0 : current + 1);
  };
  const prevSlide = () => {
    setCurrent(current === 0 ? length - 1 : current - 1);
  };

  if (!Array.isArray(slides) || slides.length <= 0) {
    return null;
  }

  return (
    <div id="gallery" className="max-w-[1240px] mx-auto">
      <h1 className="text-2xl font-bold text-center p-4">Gallery</h1>
      <div className="relative flex justify-center p-4">
        {SliderData.map((slide, index) => {
          return (
            <div
              key={index}
              className={
                index === current
                  ? "opacity-[1] ease-in duration-1000"
                  : "opacity-0"
              }
            >
              <FaArrowCircleLeft
                onClick={prevSlide}
                className="absolute top-[50%] left-[30px] text-white/70 cursor-pointer select-none z-[2]"
                size={50}
              />
              {index === current && (
                <Image
                  src={slide.image}
                  alt="/"
                  width="1440"
                  height="600"
                  objectFit="cover"
                />
              )}
              <FaArrowCircleRight
                onClick={nextSlide}
                className="absolute top-[50%] right-[30px] text-white/70 cursor-pointer select-none z-[2]"
                size={50}
              />
            </div>
          );
        })}
      </div>
    </div>
  );
};
```

--------

- Set the root to navigate to different part of the page (please do not forget to put `id="portfolio"` for smooth scrolling)
```js
<Link href="/portfolio">My roads</Link>
```

```js
const Portfolio = () => {
    return (
        <div id="portfolio" className="max-w-[1240px] mx-auto py-16 text-center">
            <h1 className="font-bold text-2xl p-4">Amazing roads</h1>
            <div className="grid grid-rows-none md:grid-cols-5 p-4 gap-4">
                <div className="w-full h-full col-span-2 md:col-span-3 row-span-2">
                    <Image
                        src="https://images.unsplash.com/photo-1520595439914-fcbb3a25d924?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1176&q=80"
                        alt="/"
                        layout="responsive"
                        width="677"
                        height="451"
                    />
```
---------


#### Reference:
- thanks goes to @Clint Briley [youtube](https://www.youtube.com/watch?v=HVyct9EUNP8), [repo](https://github.com/fireclint/NextJS-Tailwind-Responsive)
- try it out [Pesticide for Chrome](https://chrome.google.com/webstore/detail/pesticide-for-chrome/bakpbgckdnepkmkeaiomhmfcnejndkbi)
