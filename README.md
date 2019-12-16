##Burdigalax RP - Shop Exemple 

### Download only module :
[Download IHM](http://rom444.free.fr/onShop/burdigalax-shop.zip) 

### Presentation

[![Vidéo de présentation](https://img.youtube.com/vi/UWvTUOvN394/0.jpg)](https://www.youtube.com/watch?v=UWvTUOvN394)

### Live Demo

Full readme and live demo of exemple usage shop module on : http://rom444.free.fr/onShop/ 

### API

- List of issuables events : 
```
 @Burdigalax-shop:onClose
 @Burdigalax-shop:cashPayment
 @Burdigalax-shop:contactLessPayment
 @Burdigalax-shop:cardPayment
```

- List of listened events 
```
 @Burdigalax-shop:config
 @Burdigalax-shop:paymentError
 @Burdigalax-shop:paymentSuccess
 @Burdigalax-shop:resetBasket
 @Burdigalax-player:updatePlayer
 @Burdigalax-shop:updateArticles
```

##### cashPayment, contactLessPayment, cardPayment:

Object receive for these events :
```json
{
   "articles": [
      {
         "id": 7,
         "quantity": 1,
         "total": 30
      },
      {
         "id": 1,
         "quantity": 1,
         "total": 5.3
      }
   ],
   "busyStorage": 4,
   "tax": 6.32,
   "total": 35.3,
   "totalTTC": 41.62
}
```

I recommend  use only articles with id and quantity.  
**WARNING** : You must recalculate the total price on the server side for security /!\ 

##### config

Send config for show IHM :  
`window.dispatchEvent(new CustomEvent("@Burdigalax-shop:config", { detail: JSON }));`

The configuration you send will be merged with the default configuration :
- Default config : 
```json
{
   "config": {
      "hasTaxEnabled": false,
      "enabledStockLimitation": false,
      "enabledWeightControl": true,
      "maxQuantityForSelect": 50,
      "maxAmountContactLess": 300,
      "iconsUrl": {
         "addToCart": "data:image/svg+xml,%3C%3Fxml version='1.0' encoding='iso-8859-1'%3F%3E%3C!-- Generator: Adobe Illustrator 18.0.0, SVG Export Plug-In . SVG Version: 6.00 Build 0) --%3E%3C!DOCTYPE svg PUBLIC '-//W3C//DTD SVG 1.1//EN' 'http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd'%3E%3Csvg version='1.1' id='Capa_1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' x='0px' y='0px' viewBox='0 0 243.5 243.5' style='enable-background:new 0 0 243.5 243.5;' xml:space='preserve'%3E%3Cg%3E%3Cpath d='M113.403,157.775c0.399,3.858,3.655,6.729,7.451,6.729c0.258,0,0.518-0.013,0.78-0.04c4.12-0.426,7.115-4.111,6.689-8.232 l-3.458-33.468c-0.426-4.121-4.11-7.112-8.231-6.689c-4.12,0.426-7.115,4.111-6.69,8.231L113.403,157.775z'/%3E%3Cpath d='M160.338,164.464c0.262,0.027,0.522,0.04,0.78,0.04c3.795,0,7.052-2.872,7.451-6.729l3.458-33.468 c0.426-4.121-2.569-7.806-6.689-8.231c-4.121-0.422-7.806,2.57-8.232,6.689l-3.458,33.468 C153.223,160.354,156.218,164.039,160.338,164.464z'/%3E%3Cpath d='M102.266,197.064c-12.801,0-23.215,10.414-23.215,23.215c0,12.804,10.414,23.221,23.215,23.221 c12.801,0,23.216-10.417,23.216-23.221C125.481,207.479,115.067,197.064,102.266,197.064z M102.266,228.5 c-4.53,0-8.215-3.688-8.215-8.221c0-4.53,3.685-8.215,8.215-8.215c4.53,0,8.216,3.685,8.216,8.215 C110.481,224.812,106.796,228.5,102.266,228.5z'/%3E%3Cpath d='M179.707,197.064c-12.801,0-23.216,10.414-23.216,23.215c0,12.804,10.415,23.221,23.216,23.221 c12.802,0,23.218-10.417,23.218-23.221C202.925,207.479,192.509,197.064,179.707,197.064z M179.707,228.5 c-4.53,0-8.216-3.688-8.216-8.221c0-4.53,3.686-8.215,8.216-8.215c4.531,0,8.218,3.685,8.218,8.215 C187.925,224.812,184.238,228.5,179.707,228.5z'/%3E%3Cpath d='M224.569,91.057c-1.42-1.837-3.611-2.913-5.933-2.913H69.141l-6.277-24.141c-0.86-3.305-3.844-5.612-7.259-5.612h-30.74 c-4.142,0-7.5,3.358-7.5,7.5s3.358,7.5,7.5,7.5h24.941l6.221,23.922c0.034,0.15,0.073,0.299,0.116,0.446l23.15,89.022 c0.86,3.305,3.844,5.612,7.259,5.612h108.874c3.415,0,6.399-2.307,7.259-5.612l23.211-89.25 C226.478,95.285,225.989,92.894,224.569,91.057z M189.626,177.395H92.35l-19.309-74.25h135.894L189.626,177.395z'/%3E%3Cpath d='M135.674,74.826c1.464,1.464,3.384,2.197,5.303,2.197c1.92,0,3.839-0.732,5.303-2.197l24.28-24.28 c2.929-2.929,2.929-7.678,0-10.606c-2.929-2.928-7.678-2.928-10.606,0l-11.468,11.468l0.002-43.907 c0-4.142-3.357-7.501-7.499-7.501h-0.001c-4.142,0-7.5,3.358-7.5,7.499l-0.002,43.925l-11.468-11.468 c-2.929-2.929-7.678-2.929-10.606,0c-2.929,2.929-2.929,7.678,0,10.606L135.674,74.826z'/%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3C/svg%3E%0A",
         "removeToCart": "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' height='512pt' viewBox='0 0 512 512' width='512pt'%3E%3Cpath d='m256 0c-141.164062 0-256 114.835938-256 256s114.835938 256 256 256 256-114.835938 256-256-114.835938-256-256-256zm94.273438 320.105469c8.339843 8.34375 8.339843 21.824219 0 30.167969-4.160157 4.160156-9.621094 6.25-15.085938 6.25-5.460938 0-10.921875-2.089844-15.082031-6.25l-64.105469-64.109376-64.105469 64.109376c-4.160156 4.160156-9.621093 6.25-15.082031 6.25-5.464844 0-10.925781-2.089844-15.085938-6.25-8.339843-8.34375-8.339843-21.824219 0-30.167969l64.109376-64.105469-64.109376-64.105469c-8.339843-8.34375-8.339843-21.824219 0-30.167969 8.34375-8.339843 21.824219-8.339843 30.167969 0l64.105469 64.109376 64.105469-64.109376c8.34375-8.339843 21.824219-8.339843 30.167969 0 8.339843 8.34375 8.339843 21.824219 0 30.167969l-64.109376 64.105469zm0 0'/%3E%3C/svg%3E",
         "paymentCash": "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' version='1.1' id='Capa_1' x='0px' y='0px' viewBox='0 0 478.856 478.856' style='enable-background:new 0 0 478.856 478.856;' xml:space='preserve'%3E%3Cg%3E%3Cg%3E%3Cpath d='M406.872,160.017c-0.005,0-0.011,0-0.016,0h-400c-3.782-0.004-6.852,3.058-6.856,6.84c0,0.005,0,0.011,0,0.016v192 c-0.004,3.782,3.058,6.852,6.84,6.856c0.005,0,0.011,0,0.016,0h272c3.786,0,6.856-3.07,6.856-6.856 c0-3.786-3.07-6.856-6.856-6.856H13.712V173.729H400v17.144c-0.004,3.782,3.058,6.852,6.84,6.856c0.005,0,0.011,0,0.016,0 c3.782,0.004,6.852-3.058,6.856-6.84c0-0.005,0-0.011,0-0.016v-24C413.716,163.091,410.654,160.022,406.872,160.017z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M360.36,128.185l-320-72c-1.776-0.397-3.637-0.075-5.176,0.896c-1.537,0.979-2.624,2.526-3.024,4.304l-16,72 c-0.822,3.698,1.51,7.362,5.208,8.184c3.698,0.822,7.362-1.51,8.184-5.208l14.504-65.288l313.296,70.488 c0.496,0.115,1.003,0.172,1.512,0.168c3.786-0.007,6.85-3.082,6.844-6.868C365.702,131.66,363.482,128.89,360.36,128.185z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M321.504,88.513l-192-80c-3.337-1.391-7.182,0.038-8.8,3.272l-16,32c-1.807,3.342-0.563,7.517,2.78,9.324 c3.342,1.807,7.517,0.563,9.324-2.78c0.071-0.131,0.138-0.265,0.2-0.401v0.016l13.128-26.272l186.072,77.528 c3.504,1.462,7.53-0.192,8.992-3.696C326.662,94.002,325.008,89.976,321.504,88.513z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M326.352,192.017h-63.496c-3.786,0-6.856,3.07-6.856,6.856c0,3.786,3.07,6.856,6.856,6.856h63.496 c3.786,0,6.856-3.07,6.856-6.856S330.138,192.017,326.352,192.017z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M198.856,192.473c-38.881,0-70.4,31.519-70.4,70.4c0.04,38.864,31.536,70.36,70.4,70.4c38.881,0,70.4-31.519,70.4-70.4 S237.737,192.473,198.856,192.473z M198.856,320.473c-31.812,0-57.6-25.788-57.6-57.6c0.035-31.797,25.803-57.565,57.6-57.6 c31.812,0,57.6,25.788,57.6,57.6C256.456,294.685,230.668,320.473,198.856,320.473z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M390.856,214.873c-42.4,0-88,10.016-88,32v192c0,21.984,45.6,32,88,32c42.4,0,88-10.016,88-32v-192 C478.856,224.889,433.256,214.873,390.856,214.873z M462.856,438.753c-1.208,4.44-25.2,16.12-72,16.12s-70.792-11.68-72-16 v-12.576c17.024,8.576,45.144,12.576,72,12.576c26.856,0,54.984-4.04,72-12.584V438.753z M462.856,406.753 c-1.208,4.44-25.2,16.12-72,16.12s-70.792-11.68-72-16v-12.576c17.024,8.576,45.144,12.576,72,12.576 c26.856,0,54.984-4.04,72-12.584V406.753z M462.856,374.753c-1.208,4.44-25.2,16.12-72,16.12s-70.792-11.68-72-16v-12.576 c17.024,8.576,45.144,12.576,72,12.576c26.856,0,54.984-4.04,72-12.584V374.753z M462.856,342.753 c-1.208,4.44-25.2,16.12-72,16.12s-70.792-11.68-72-16v-12.576c17.024,8.576,45.144,12.576,72,12.576 c26.856,0,54.984-4.04,72-12.584V342.753z M462.856,310.753c-1.208,4.44-25.2,16.12-72,16.12s-70.792-11.68-72-16v-12.576 c17.024,8.536,45.144,12.576,72,12.576c26.856,0,54.984-4.04,72-12.584V310.753z M462.856,278.753 c-1.208,4.44-25.2,16.12-72,16.12s-70.792-11.68-72-16v-12.576c17.024,8.536,45.144,12.576,72,12.576 c26.856,0,54.984-4.04,72-12.584V278.753z M390.856,262.873c-46.728,0-70.712-11.648-72-15.856v-0.048 c1.288-4.456,25.272-16.096,72-16.096c46.4,0,70.4,11.472,72,16C461.256,251.401,437.256,262.873,390.856,262.873z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M134.856,320.009H74.384l-28.672-31.36v-52l31.664-30.92h57.48c3.786,0,6.856-3.07,6.856-6.856 c0-3.786-3.07-6.856-6.856-6.856H74.592c-1.792-0.004-3.515,0.694-4.8,1.944l-35.736,34.856c-1.335,1.56-2.067,3.547-2.064,5.6 v56.896c0,1.711,0.639,3.36,1.792,4.624l32.504,35.552c1.299,1.422,3.137,2.233,5.064,2.232h63.504 c3.786,0,6.856-3.07,6.856-6.856C141.712,323.079,138.643,320.009,134.856,320.009z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M202.856,254.873h-8c-2.488,0-4-1.392-4-2c0-0.608,1.512-2,4-2h20c4.418,0,8-3.582,8-8s-3.582-8-8-8h-8 c0-4.418-3.582-8-8-8s-8,3.582-8,8v0.36c-8.873,1.253-15.595,8.648-16,17.6c0.573,10.489,9.507,18.548,20,18.04h8 c2.488,0,4,1.392,4,2c0,0.608-1.512,2-4,2h-20c-4.418,0-8,3.582-8,8s3.582,8,8,8h8c0,4.418,3.582,8,8,8s8-3.582,8-8v-0.36 c8.873-1.253,15.595-8.648,16-17.6C222.283,262.424,213.349,254.365,202.856,254.873z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3C/svg%3E",
         "paymentContactLess": "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' height='512' viewBox='0 0 57 60' width='512'%3E%3Cg id='075---Contactless'%3E%3Cpath id='Shape' d='m5 60h28c2.7614237 0 5-2.2385763 5-5v-50c0-2.76142375-2.2385763-5-5-5h-28c-2.76142375 0-5 2.23857625-5 5v50c0 2.7614237 2.23857625 5 5 5zm31-55v50c0 1.6568542-1.3431458 3-3 3h-2v-56h2c1.6568542 0 3 1.34314575 3 3zm-7-3v56h-6v-56zm-27 3c0-1.65685425 1.34314575-3 3-3h16v56h-16c-1.65685425 0-3-1.3431458-3-3z'/%3E%3Cpath id='Shape' d='m7 15h4c1.1045695 0 2-.8954305 2-2v-6c0-1.1045695-.8954305-2-2-2h-4c-1.1045695 0-2 .8954305-2 2v6c0 1.1045695.8954305 2 2 2zm0-8h4v6h-4z'/%3E%3Cpath id='Shape' d='m9 55c1.539412-.0017181 2.9412388-.8866992 3.6048229-2.2757451s.4711597-3.0356432-.4948229-4.2342549c1.320829-1.6329662 1.1537594-4.0093602-.3825554-5.4414583-1.5363148-1.432098-3.91857443-1.432098-5.45488922 0-1.53631478 1.4320981-1.7033844 3.8084921-.38255538 5.4414583-.96598261 1.1986117-1.15840704 2.845209-.49482291 4.2342549s2.06541087 2.274027 3.60482291 2.2757451zm0-2c-.77889693-.0038352-1.48471194-.4595256-1.80880346-1.1678051s-.20749512-1.5402854.29880346-2.1321949c.96213064.389201 2.03786936.389201 3 0 .5040737.5891546.6222013 1.4165734.303128 2.1232457-.3190732.7066723-1.01784667 1.1652479-1.793128 1.1767543zm0-9c1.1045695 0 2 .8954305 2 2s-.8954305 2-2 2-2-.8954305-2-2 .8954305-2 2-2z'/%3E%3Cpath id='Shape' d='m50.18 41.6c-.2884599.2860905-.3751619.7182668-.219371 1.0934815.155791.3752147.5231059.6188811.929371.6165185.2687063-.0037358.5246007-.1154643.71-.31 7.1198971-7.1419827 7.1198971-18.6980173 0-25.84-.3921222-.3921221-1.0278778-.3921221-1.42 0-.3921221.3921222-.3921221 1.0278778 0 1.42 3.0545049 3.0516526 4.7707479 7.1922941 4.7707479 11.51s-1.716243 8.4583474-4.7707479 11.51z'/%3E%3Cpath id='Shape' d='m46.7 20.67c-.1893127.1877666-.2957983.4433625-.2957983.71s.1064856.5222334.2957983.71c4.4093025 4.421992 4.4093025 11.578008 0 16-.3921221.3893608-.3943607 1.0228778-.005 1.415.3893608.3921221 1.0228778.3943607 1.415.005 5.2003457-5.2112321 5.2003457-13.6487679 0-18.86-.3955152-.3822465-1.0254856-.3733107-1.41.02z'/%3E%3Cpath id='Shape' d='m43.21 36c.3900375.3877236 1.0199625.3877236 1.41 0 1.575491-1.5753302 2.4606061-3.712033 2.4606061-5.94s-.8851151-4.3646698-2.4606061-5.94c-.3900375-.3877236-1.0199625-.3877236-1.41 0-.1893127.1877666-.2957983.4433625-.2957983.71s.1064856.5222334.2957983.71c2.4877279 2.5037835 2.4877279 6.5462165 0 9.05-.3877236.3900375-.3877236 1.0199625 0 1.41z'/%3E%3C/g%3E%3C/svg%3E",
         "paymentCard": "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' version='1.1' id='Capa_1' x='0px' y='0px' viewBox='0 0 480 480' style='enable-background:new 0 0 480 480;' xml:space='preserve'%3E%3Cg%3E%3Cg%3E%3Cpath d='M416,0H208c-13.255,0-24,10.745-24,24v92.056l-81.456,62.528c-8.728,5.477-14.992,14.126-17.472,24.128L42.152,374.4 c-1.432,5.716-2.155,11.587-2.152,17.48V480h16v-88.12c-0.003-4.585,0.559-9.152,1.672-13.6L100.6,206.576 c1.519-6.074,5.363-11.308,10.704-14.576c0.232-0.144,0.456-0.304,0.68-0.464l72-55.28v100.432l-29.656,29.656l11.312,11.312 l103.728-103.712c7.924-7.922,20.77-7.92,28.692,0.004c3.803,3.804,5.94,8.962,5.94,14.34v1.248 c0.01,4.771-1.671,9.391-4.744,13.04l-65.192,72.056c-1.613,1.787-2.336,4.205-1.968,6.584l0.608,4 c8,52.08-21.52,97.304-75.2,115.2l5.056,15.2c23.397-7.425,44.309-21.128,60.456-39.616h57.6l-30.12,43.024 c-10.17,14.581-24.537,25.72-41.192,31.936l-36.128,13.544c-3.118,1.177-5.181,4.163-5.176,7.496v8h16v-2.456l30.936-11.6 c19.682-7.352,36.662-20.516,48.688-37.744l36.544-52.2H416c13.255,0,24-10.745,24-24V24C440,10.745,429.255,0,416,0z M424,352 c0,4.418-3.582,8-8,8H234.4c13.57-23.309,18.554-50.633,14.088-77.232v-0.224l62.776-69.392 c5.634-6.579,8.732-14.954,8.736-23.616v-1.248c0.007-20.037-16.231-36.286-36.268-36.292 c-9.631-0.003-18.869,3.823-25.676,10.636L200,220.688V24c0-4.418,3.582-8,8-8h208c4.418,0,8,3.582,8,8V352z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M394.512,91.856C398.064,85.839,399.957,78.987,400,72c0-22.091-17.909-40-40-40c-22.091,0-40,17.909-40,40 c0.043,6.987,1.936,13.839,5.488,19.856c-11.161,19.024-4.786,43.493,14.238,54.654c6.147,3.606,13.147,5.502,20.274,5.49 c22.056,0.036,39.966-17.814,40.002-39.87C400.014,105.003,398.118,98.003,394.512,91.856z M367.63,134.812 c-2.462,0.809-5.039,1.211-7.63,1.188c-13.131,0.122-23.874-10.423-23.996-23.554c-0.024-2.596,0.377-5.179,1.188-7.646 c13.68,9.613,31.92,9.613,45.6,0C386.893,117.274,380.104,130.711,367.63,134.812z M360,96c-13.255,0-24-10.745-24-24 s10.745-24,24-24s24,10.745,24,24S373.255,96,360,96z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Crect x='216' y='48' width='16' height='120'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Crect x='248' y='56' width='16' height='80'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Crect x='304' y='240' width='16' height='32'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Crect x='304' y='288' width='16' height='40'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Crect x='360' y='176' width='16' height='160'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Crect x='392' y='176' width='16' height='160'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3C/svg%3E",
         "emptyBasket": "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 -36 512.001 512'%3E%3Cpath d='m256 219.988281c5.519531 0 10-4.480469 10-10s-4.480469-10-10-10-10 4.480469-10 10 4.480469 10 10 10zm0 0'/%3E%3Cpath d='m472 139.988281h-59.136719l-90.96875-125.152343c-8.171875-14.003907-26.171875-18.988282-40.46875-11.070313-14.492187 8.050781-19.703125 26.304687-11.648437 40.800781.230468.410156.484375.804688.769531 1.179688l71.351563 94.242187h-171.796876l71.351563-94.242187c.28125-.375.539063-.769532.769531-1.179688 8.035156-14.460937 2.882813-32.730468-11.660156-40.808594-14.265625-7.902343-32.265625-2.921874-40.453125 11.070313l-90.972656 125.160156h-59.136719c-22.054688 0-40 17.945313-40 40 0 17.394531 11.289062 32.539063 27.191406 37.898438 1.695313 1.3125 3.8125 2.101562 6.117188 2.101562.460937 0 .894531.027344 1.347656.089844 4.304688.578125 7.714844 3.84375 8.496094 8.117187l34.019531 187.164063c2.597656 14.269531 15.011719 24.628906 29.519531 24.628906h298.617188c14.507812 0 26.921875-10.359375 29.519531-24.632812l34.019531-187.15625c.78125-4.277344 4.195313-7.542969 8.515625-8.121094.4375-.0625.871094-.089844 1.328125-.089844 2.320313 0 4.453125-.796875 6.148438-2.125 15.914062-5.394531 27.160156-20.511719 27.160156-37.875 0-22.054687-17.945312-40-40-40zm-185.011719-105.660156c-2.285156-4.730469-.511719-10.492187 4.136719-13.070313 4.839844-2.683593 10.941406-.953124 13.609375 3.855469.195313.359375.417969.703125.65625 1.03125l82.746094 113.84375h-21.15625zm-80.378906-8.179687c.238281-.328126.453125-.667969.652344-1.019532 2.675781-4.8125 8.78125-6.546875 13.601562-3.878906 4.65625 2.585938 6.4375 8.339844 4.148438 13.078125l-79.992188 105.660156h-21.15625zm265.390625 173.839843h-176c-5.523438 0-10 4.476563-10 10 0 5.523438 4.476562 9.898438 10 9.898438h154.398438c-.523438 1.492187-.9375 3.039062-1.226563 4.632812l-34.023437 187.257813c-.863282 4.757812-5.003907 8.210937-9.839844 8.210937h-298.617188c-4.839844 0-8.976562-3.453125-9.84375-8.207031l-34.019531-187.164062c-.289063-1.59375-.703125-3.140626-1.226563-4.628907h154.398438c5.523438 0 10-4.476562 10-10 0-5.523437-4.476562-10-10-10h-176c-11.121094 0-20-9.0625-20-20 0-11.027343 8.972656-20 20-20h432c11.027344 0 20 8.972657 20 20 0 11.105469-9.085938 20-20 20zm0 0'/%3E%3Cpath d='m256 249.988281c-16.542969 0-30 13.457031-30 30v80c0 16.542969 13.457031 30 30 30s30-13.457031 30-30v-80c0-16.574219-13.425781-30-30-30zm10 110c0 5.515625-4.484375 10-10 10s-10-4.484375-10-10v-80c0-5.515625 4.484375-10 10-10 5.519531 0 10 4.480469 10 10zm0 0'/%3E%3Cpath d='m356 389.988281c16.542969 0 30-13.457031 30-30v-80c0-16.574219-13.425781-30-30-30-16.542969 0-30 13.457031-30 30v80c0 16.542969 13.457031 30 30 30zm-10-110c0-5.515625 4.484375-10 10-10 5.519531 0 10 4.480469 10 10v80c0 5.515625-4.484375 10-10 10s-10-4.484375-10-10zm0 0'/%3E%3Cpath d='m156 249.988281c-16.542969 0-30 13.457031-30 30v80c0 16.542969 13.457031 30 30 30s30-13.457031 30-30v-80c0-16.574219-13.425781-30-30-30zm10 110c0 5.515625-4.484375 10-10 10s-10-4.484375-10-10v-80c0-5.515625 4.484375-10 10-10 5.519531 0 10 4.476563 10 10zm0 0'/%3E%3C/svg%3E",
         "emptyBox": "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' version='1.1' id='Capa_1' x='0px' y='0px' width='59.227px' height='59.227px' viewBox='0 0 59.227 59.227' style='enable-background:new 0 0 59.227 59.227;' xml:space='preserve'%3E%3Cg%3E%3Cg%3E%3Cpath d='M51.586,10.029c-0.333-0.475-0.897-0.689-1.449-0.607c-0.021-0.005-0.042-0.014-0.063-0.017L27.469,6.087 c-0.247-0.037-0.499-0.01-0.734,0.076L8.63,12.799c-0.008,0.003-0.015,0.008-0.023,0.011c-0.019,0.008-0.037,0.02-0.057,0.027 c-0.099,0.044-0.191,0.096-0.276,0.157c-0.026,0.019-0.051,0.038-0.077,0.059c-0.093,0.076-0.178,0.159-0.249,0.254 c-0.004,0.006-0.01,0.009-0.014,0.015L0.289,23.78c-0.293,0.401-0.369,0.923-0.202,1.391c0.167,0.469,0.556,0.823,1.038,0.947 l6.634,1.713v16.401c0,0.659,0.431,1.242,1.062,1.435l24.29,7.422c0.008,0.004,0.017,0.001,0.025,0.005 c0.13,0.036,0.266,0.059,0.402,0.06c0.003,0,0.007,0.002,0.011,0.002l0,0h0.001c0.143,0,0.283-0.026,0.423-0.067 c0.044-0.014,0.085-0.033,0.13-0.052c0.059-0.022,0.117-0.038,0.175-0.068l17.43-9.673c0.477-0.265,0.772-0.767,0.772-1.312 V25.586l5.896-2.83c0.397-0.19,0.69-0.547,0.802-0.973c0.111-0.427,0.03-0.88-0.223-1.241L51.586,10.029z M27.41,9.111 l17.644,2.59L33.35,17.143l-18.534-3.415L27.41,9.111z M9.801,15.854l21.237,3.914l-6.242,9.364l-20.78-5.365L9.801,15.854z M10.759,43.122V28.605l14.318,3.697c0.125,0.031,0.25,0.048,0.375,0.048c0.493,0,0.965-0.244,1.248-0.668l5.349-8.023v25.968 L10.759,43.122z M49.479,41.1l-14.431,8.007V25.414l2.635,5.599c0.171,0.361,0.479,0.641,0.854,0.773 c0.163,0.06,0.333,0.087,0.502,0.087c0.223,0,0.444-0.05,0.649-0.146l9.789-4.698L49.479,41.1L49.479,41.1z M39.755,28.368 l-4.207-8.938L49.85,12.78l5.634,8.037L39.755,28.368z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3C/svg%3E",
         "breakdown": "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' version='1.1' id='Capa_1' x='0px' y='0px' viewBox='0 0 231.233 231.233' style='enable-background:new 0 0 231.233 231.233;' xml:space='preserve'%3E%3Cpath d='M230.505,102.78c-0.365-3.25-4.156-5.695-7.434-5.695c-10.594,0-19.996-6.218-23.939-15.842 c-4.025-9.855-1.428-21.346,6.465-28.587c2.486-2.273,2.789-6.079,0.705-8.721c-5.424-6.886-11.586-13.107-18.316-18.498 c-2.633-2.112-6.502-1.818-8.787,0.711c-6.891,7.632-19.27,10.468-28.836,6.477c-9.951-4.187-16.232-14.274-15.615-25.101 c0.203-3.403-2.285-6.36-5.676-6.755c-8.637-1-17.35-1.029-26.012-0.068c-3.348,0.37-5.834,3.257-5.723,6.617 c0.375,10.721-5.977,20.63-15.832,24.667c-9.451,3.861-21.744,1.046-28.621-6.519c-2.273-2.492-6.074-2.798-8.725-0.731 c-6.928,5.437-13.229,11.662-18.703,18.492c-2.133,2.655-1.818,6.503,0.689,8.784c8.049,7.289,10.644,18.879,6.465,28.849 c-3.99,9.505-13.859,15.628-25.156,15.628c-3.666-0.118-6.275,2.345-6.68,5.679c-1.016,8.683-1.027,17.535-0.049,26.289 c0.365,3.264,4.268,5.688,7.582,5.688c10.07-0.256,19.732,5.974,23.791,15.841c4.039,9.855,1.439,21.341-6.467,28.592 c-2.473,2.273-2.789,6.07-0.701,8.709c5.369,6.843,11.537,13.068,18.287,18.505c2.65,2.134,6.504,1.835,8.801-0.697 c6.918-7.65,19.295-10.481,28.822-6.482c9.98,4.176,16.258,14.262,15.645,25.092c-0.201,3.403,2.293,6.369,5.672,6.755 c4.42,0.517,8.863,0.773,13.32,0.773c4.23,0,8.461-0.231,12.692-0.702c3.352-0.37,5.834-3.26,5.721-6.621 c-0.387-10.716,5.979-20.626,15.822-24.655c9.514-3.886,21.752-1.042,28.633,6.512c2.285,2.487,6.063,2.789,8.725,0.73 c6.916-5.423,13.205-11.645,18.703-18.493c2.135-2.65,1.832-6.503-0.689-8.788c-8.047-7.284-10.656-18.879-6.477-28.839 c3.928-9.377,13.43-15.673,23.65-15.673l1.43,0.038c3.318,0.269,6.367-2.286,6.768-5.671 C231.476,120.379,231.487,111.537,230.505,102.78z M115.616,182.27c-36.813,0-66.654-29.841-66.654-66.653 s29.842-66.653,66.654-66.653s66.654,29.841,66.654,66.653c0,12.495-3.445,24.182-9.428,34.176l-29.186-29.187 c2.113-4.982,3.229-10.383,3.228-15.957c0-10.915-4.251-21.176-11.97-28.893c-7.717-7.717-17.978-11.967-28.891-11.967 c-3.642,0-7.267,0.484-10.774,1.439c-1.536,0.419-2.792,1.685-3.201,3.224c-0.418,1.574,0.053,3.187,1.283,4.418 c0,0,14.409,14.52,19.23,19.34c0.505,0.505,0.504,1.71,0.433,2.144l-0.045,0.317c-0.486,5.3-1.423,11.662-2.196,14.107 c-0.104,0.103-0.202,0.19-0.308,0.296c-0.111,0.111-0.213,0.218-0.32,0.328c-2.477,0.795-8.937,1.743-14.321,2.225l0.001-0.029 l-0.242,0.061c-0.043,0.005-0.123,0.011-0.229,0.011c-0.582,0-1.438-0.163-2.216-0.94c-5.018-5.018-18.862-18.763-18.862-18.763 c-1.242-1.238-2.516-1.498-3.365-1.498c-1.979,0-3.751,1.43-4.309,3.481c-3.811,14.103,0.229,29.273,10.546,39.591 c7.719,7.718,17.981,11.968,28.896,11.968c5.574,0,10.975-1.115,15.956-3.228l29.503,29.503 C141.125,178.412,128.825,182.27,115.616,182.27z'/%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3C/svg%3E",
         "weight": "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' version='1.1' id='Capa_1' x='0px' y='0px' viewBox='0 0 511.999 511.999' style='enable-background:new 0 0 511.999 511.999;' xml:space='preserve'%3E%3Cg%3E%3Cg%3E%3Cpath d='M503.058,157.279l-42.338-42.338l31.827-31.815c2.814-2.811,4.396-6.62,4.396-10.604c0-3.984-1.582-7.793-4.395-10.605 l-42.612-42.612c-5.625-5.625-15.586-5.625-21.211,0L396.91,51.132L354.566,8.786c-11.715-11.715-30.71-11.715-42.426,0 c-11.717,11.715-11.717,30.71,0,42.426l148.491,148.493c11.717,11.715,30.712,11.715,42.427,0 C514.773,187.99,514.773,168.995,503.058,157.279z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M199.86,460.786L51.369,312.293c-11.717-11.715-30.71-11.715-42.427,0c-11.715,11.717-11.715,30.712,0,42.427 l42.345,42.345l-31.765,31.752c-2.813,2.813-4.395,6.621-4.395,10.605s1.582,7.793,4.395,10.605l42.612,42.598 c2.929,2.931,6.767,4.396,10.605,4.396s7.676-1.465,10.605-4.395l31.752-31.752l42.338,42.339 c11.715,11.715,30.71,11.715,42.426,0C211.577,491.496,211.577,472.501,199.86,460.786z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpolygon points='269.713,178.492 178.647,269.868 242.287,333.508 333.353,242.13 '/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M460.632,242.131L269.713,51.212c-11.715-11.715-30.711-11.715-42.426,0c-11.717,11.717-11.717,30.71,0,42.427 l190.919,190.919c11.715,11.715,30.71,11.715,42.426,0C472.349,272.843,472.349,253.848,460.632,242.131z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M284.714,418.36L93.794,227.44c-11.715-11.715-30.71-11.715-42.425,0c-11.717,11.717-11.717,30.712,0,42.427 l190.919,190.919c11.715,11.715,30.71,11.715,42.426,0C296.431,449.071,296.431,430.076,284.714,418.36z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3C/svg%3E",
         "successPayment": "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' version='1.1' id='Capa_1' x='0px' y='0px' viewBox='0 0 52 52' style='enable-background:new 0 0 52 52;' xml:space='preserve'%3E%3Cg%3E%3Cpath d='M26,0C11.664,0,0,11.663,0,26s11.664,26,26,26s26-11.663,26-26S40.336,0,26,0z M40.495,17.329l-16,18 C24.101,35.772,23.552,36,22.999,36c-0.439,0-0.88-0.144-1.249-0.438l-10-8c-0.862-0.689-1.002-1.948-0.312-2.811 c0.689-0.863,1.949-1.003,2.811-0.313l8.517,6.813l14.739-16.581c0.732-0.826,1.998-0.9,2.823-0.166 C41.154,15.239,41.229,16.503,40.495,17.329z'/%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3C/svg%3E",
         "errorPayment": "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' version='1.1' id='Capa_1' x='0px' y='0px' viewBox='0 0 28 28' style='enable-background:new 0 0 28 28;' xml:space='preserve'%3E%3Cg%3E%3Cg id='x'%3E%3Cg%3E%3Cpolygon style='fill:%23030104;' points='28,22.398 19.594,14 28,5.602 22.398,0 14,8.402 5.598,0 0,5.602 8.398,14 0,22.398 5.598,28 14,19.598 22.398,28 '/%3E%3C/g%3E%3C/g%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3C/svg%3E"
      },
      "style": {
         "backgroundColor": "#2a6041",
         "headerBackgroundColor": "#5da95708",
         "titleColor": "#86a593",
         "greenColor": "#28a745",
         "redColor": "#d02e22",
         "basketBackgroundColor": "#acd4bc"
      },
      "wording": {
         "informations": "Informations",
         "descriptionInformations": "Cliquer sur un produit pour avoir des informations supplémentaires.",
         "noInformation": "Aucune information",
         "effects": "Effets",
         "article": "Article",
         "priceExcludingTax": "Prix HT",
         "price": "Prix",
         "taxName": "TVA",
         "unitPrice": "Prix U",
         "quantity": "Quantité",
         "action": "Action",
         "basket": "Panier",
         "emptyBasket": "Panier vide",
         "totalExcludingTax": "Total HT",
         "totalAll": "Total TTC",
         "total": "Total",
         "moneySymbol": "$",
         "basketArticles": "articles",
         "backBasket": "Retour au panier"
      }
   },
   "player": {},
   "shop": {
      "name": "On7/7",
      "iconUrl": "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' version='1.1' id='Layer_1' x='0px' y='0px' viewBox='0 0 511.999 511.999' style='enable-background:new 0 0 511.999 511.999;' xml:space='preserve'%3E%3Cg%3E%3Cg%3E%3Cpath d='M214.685,402.828c-24.829,0-45.029,20.2-45.029,45.029c0,24.829,20.2,45.029,45.029,45.029s45.029-20.2,45.029-45.029 C259.713,423.028,239.513,402.828,214.685,402.828z M214.685,467.742c-10.966,0-19.887-8.922-19.887-19.887 c0-10.966,8.922-19.887,19.887-19.887s19.887,8.922,19.887,19.887C234.572,458.822,225.65,467.742,214.685,467.742z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M372.63,402.828c-24.829,0-45.029,20.2-45.029,45.029c0,24.829,20.2,45.029,45.029,45.029s45.029-20.2,45.029-45.029 C417.658,423.028,397.458,402.828,372.63,402.828z M372.63,467.742c-10.966,0-19.887-8.922-19.887-19.887 c0-10.966,8.922-19.887,19.887-19.887c10.966,0,19.887,8.922,19.887,19.887C392.517,458.822,383.595,467.742,372.63,467.742z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M383.716,165.755H203.567c-6.943,0-12.571,5.628-12.571,12.571c0,6.943,5.629,12.571,12.571,12.571h180.149 c6.943,0,12.571-5.628,12.571-12.571C396.287,171.382,390.659,165.755,383.716,165.755z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M373.911,231.035H213.373c-6.943,0-12.571,5.628-12.571,12.571s5.628,12.571,12.571,12.571h160.537 c6.943,0,12.571-5.628,12.571-12.571C386.481,236.664,380.853,231.035,373.911,231.035z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cpath d='M506.341,109.744c-4.794-5.884-11.898-9.258-19.489-9.258H95.278L87.37,62.097c-1.651-8.008-7.113-14.732-14.614-17.989 l-55.177-23.95c-6.37-2.767-13.773,0.156-16.536,6.524c-2.766,6.37,0.157,13.774,6.524,16.537L62.745,67.17l60.826,295.261 c2.396,11.628,12.752,20.068,24.625,20.068h301.166c6.943,0,12.571-5.628,12.571-12.571c0-6.943-5.628-12.571-12.571-12.571 H148.197l-7.399-35.916H451.69c11.872,0,22.229-8.44,24.624-20.068l35.163-170.675 C513.008,123.266,511.136,115.627,506.341,109.744z M451.69,296.301H135.619l-35.161-170.674l386.393,0.001L451.69,296.301z'/%3E%3C/g%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3Cg%3E%3C/g%3E%3C/svg%3E",
      "hasPaymentTerminalBroken": false,
      "articles": []
   },
   "effects": {}
}
```

- List of all editable parameters :

```json
{
   "config": {
      "hasTaxEnabled": true,
      "enabledStockLimitation": true,
      "enabledWeightControl": true,
      "maxQuantityForSelect": 50,
      "maxAmountContactLess": 300,
      "iconsUrl": {
         "addToCart": "dataURI",
         "removeToCart": "dataURI",
         "paymentCash": "dataURI",
         "paymentContactLess": "dataURI",
         "paymentCard":"dataURI",
         "emptyBasket": "dataURI",
         "emptyBox": "dataURI",
         "breakdown": "dataURI",
         "weight": "dataURI",
         "successPayment": "dataURI",
         "errorPayment": "dataURI"
      },
      "style": {
         "backgroundColor": "#2a6041",
         "headerBackgroundColor": "#5da95708",
         "titleColor": "#86a593",
         "greenColor": "#28a745",
         "redColor": "#d02e22",
         "basketBackgroundColor": "#acd4bc"
      },
      "wording": {
         "informations": "Informations",
         "descriptionInformations": "Cliquer sur un produit pour avoir des informations supplémentaires.",
         "noInformation": "Aucune information",
         "effects": "Effets",
         "article": "Article",
         "priceExcludingTax": "Prix HT",
         "price": "Prix",
         "taxName": "TVA",
         "unitPrice": "Prix U",
         "quantity": "Quantité",
         "action": "Action",
         "basket": "Panier",
         "emptyBasket": "Panier vide",
         "totalExcludingTax": "Total HT",
         "totalAll": "Total TTC",
         "total": "Total",
         "moneySymbol": "$",
         "basketArticles": "articles",
         "backBasket": "Retour au panier"
      }
   },
   "player": {
      "money": {
         "cash": 300
      },
      "freeStorageSpace": 20
   },
   "shop": {
      "name": "On7/7",
      "iconUrl": "dataURI",
      "hasPaymentTerminalBroken": true,
      "articles": [
         {
            "id": 1,
            "name": "Bouteille d'eau",
            "price": 5,
            "quantity": 100,
            "description": "Eau de la ville, avec un léger coût de javel.",
            "iconUrl": "dataURI",
            "storageCost": 2,
            "tax": 6,
            "effects": [
               {
                  "id": "hydration",
                  "value": 40
               }
            ]
         },
         {
            "id": 7,
            "name": "Bandage",
            "price": 25,
            "quantity": 25,
            "description": "",
            "iconUrl": "dataURI",
            "storageCost": 2,
            "tax": 20,
            "effects": [
               {
                  "id": "bleeding",
                  "value": -70
               }
            ]
         },
         {
            "id": 6,
            "name": "Jerrican d'essence",
            "price": 50,
            "quantity": 2,
            "description": "",
            "iconUrl": "dataURI",
            "storageCost": 5,
            "tax": 35,
            "effects": [
               {
                  "id": "petrol",
                  "value": 15
               }
            ]
         },
         {
            "id": 4,
            "name": "Médicament",
            "price": 15,
            "quantity": 10,
            "description": "",
            "iconUrl": "dataURI",
            "storageCost": 2,
            "tax": 20,
            "effects": [
               {
                  "id": "health",
                  "value": 20
               }
            ]
         },
         {
            "id": 5,
            "name": "Chocolatine",
            "price": 1,
            "quantity": 50,
            "description": "",
            "iconUrl": "dataURI",
            "storageCost": 1,
            "tax": 6,
            "effects": [
               {
                  "id": "food",
                  "value": 20
               },
               {
                  "id": "hydration",
                  "value": -5
               }
            ]
         },
         {
            "id": 2,
            "name": "Pomme",
            "price": 0.5,
            "quantity": 5,
            "description": "",
            "iconUrl": "dataURI",
            "storageCost": 1,
            "tax": -15,
            "effects": [
               {
                  "id": "food",
                  "value": 7
               },
               {
                  "id": "hydration",
                  "value": 5
               }
            ]
         },
         {
            "id": 3,
            "name": "Téléphone",
            "price": 500,
            "quantity": 0,
            "description": "",
            "iconUrl": "dataURI",
            "storageCost": 1,
            "tax": 20
         }
      ]
   },
   "effects": {
      "hydration": {
         "name": "Hydratation",
         "unit": "%",
         "iconUrl": "dataURI"
      },
      "petrol": {
         "name": "Essence",
         "unit": "L",
         "iconUrl": "dataURI"
      },
      "food": {
         "name": "Alimentation",
         "iconUrl": "dataURI",
         "unit": "%"
      },
      "health": {
         "name": "Santé",
         "iconUrl": "dataURI",
         "unit": "%"
      },
      "bleeding": {
         "name": "Saignement",
         "iconUrl": "dataURI",
         "unit": "%"
      }
   }
}
```

#### paymentError

```js
window.dispatchEvent(new CustomEvent("@Burdigalax-shop:paymentError", { detail: 
  { title: 'Erreur', message: "Vous n'avez pas assez d'argent", iconUrl: "//Optional use for override config."} 
}));
```

#### paymentSuccess

```js 
window.dispatchEvent(new CustomEvent("@Burdigalax-shop:paymentSuccess", { detail: 
  { title: 'Félicitation', message: "Paiement validé", iconUrl: "//Optional use for override config."} 
}));
```

#### resetBasket

```js 
window.dispatchEvent(new CustomEvent("@Burdigalax-shop:resetBasket"));
```

#### updatePlayer

```js 
window.dispatchEvent(new CustomEvent("@Burdigalax-player:updatePlayer", { detail: 
  {
     "money": {
        "cash": 500
     },
     "freeStorageSpace": 200
  } 
}));
```

#### updateArticles 

**WARNING:** Update Articles not update basket for this moment. I recommend using it with action : @Burdigalax-shop:resetBasket

```js 
window.dispatchEvent(new CustomEvent("@Burdigalax-shop:updateArticles", { detail: 
  [
    {
        "id": 1,
        "quantity": 10,
    },
  ]
}));
```
### Contact
> Discord: RomBurdi#9770