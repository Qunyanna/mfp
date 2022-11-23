{
 "cells": [
  {
   "cell_type": "markdown",
   "id": "e375bacb",
   "metadata": {},
   "source": [
    "# Практическая работа №1: Формирование и первичная обработка выборки. Нахождение и точечных и интервальных оценок. Проверка статистических гипотез.\n",
    "Выполнила студентка гр. 0373 Евдокимова Анна. Вариант №8 \n",
   ]
  },
  {
   "cell_type": "markdown",
   "id": "cfb94134",
   "metadata": {},
   "source": [
    "## Цель работы\n",
    "Ознакомление с основными правилами формирования выборки и подготовки выборочных данных к статистическому анализу. Получение практических навыков нахождения точечных статистических оценок параметров распределения, а также вычисления интервальных статистических оценок параметров распределения выборочных данных и проверки\n",
    "«справедливости» статистических гипотез.\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "b965d80b",
   "metadata": {},
   "source": [
    "## Основные теоретические положения\n",
    "Выборка — совокупность случайно отобранных объектов. Объем n\n",
    "\n",
    "Генеральная совокупность - совокупность объектов, из которых была произведена выборка. Объем N\n",
    "\n",
    "Интервальный вариационный ряд - весь промежуток измерения значений выборки $[x_{min},x_{max}]$ разбивают на частичные интервалы\n",
    "\n",
    "Формула Стерджеса для определения количества интервалов: $k=1+log_{2}n$\n",
    "\n",
    "Формула для нахождения длины интервала: $h=\frac{R}{k}$, где R - размах выборки: $R=x_{max}-x_{min}$\n",
    "\n",
    "Ранжированный ряд - расположение единиц совокупности в порядке возрастания или убывания выбранного признака.\n",
    "\n",
    "Вариационный ряд - ранжированный в порядке возрастания или убывания ряд вариант с соответствующими им весами\n",
    "\n",
    "Варианты - элементы выборки - $x_{i}$\n",
    "\n",
    "Абсолютные частоты - это количество раз, когда каждый элемент статистического обзора встречается - $n_{i}$\n",
    "\n",
    "Относительные частоты - отношение числа испытаний, в которых событие появилось, к общему числу фактически произведенных испытаний - $p_{i}^{*}=\frac{n_{i}}{n}$\n",
    "\n",
    "Полигон частот - ломанная линия, соединяющая точки дискретного ряда\n",
    "\n",
    "Полигон относительных частот - ломаная линия,соединяющая точки дискретного ряда $(x_{1},p_{1}^{*}),(x_{2},p_{1}^{*})... (x_{k},p_{1}^{*})$\n",
    "\n",
    "Гистограмма частот - ступенчатая фигура, состоящая из прямоугольников, основанием которых является частичные интервалы, а высоты равны $f_{i}^{*}=\frac{n_{i}^{*}}{h}$\n",
    "\n",
    "Гистограмма относительных частот - ступенчатая фигура, состоящая из прямоугольников, основанием которых является частичные интервалы, а высоты равны $f_{i}^{*}=\frac{p_{i}^{*}}{h}$\n",
    "\n",
    "Эмпирическая функция распределения - Функция $F^{*}(x)$, задающая для каждого значения х относительную частоту события ${X<x}$: $F^{*}(x)=\frac{n_{x}}{n} $ где $n_{x}$ - число выборочных значений величины X, меньших x.\n",
    "\n",
    "Накопленная абсолютная частота - число наблюдений, при которых наблюдалось значение признака, меньшее $х_{i}$\n",
    "\n",
    "Накопленные относительные частоты - отношениче накопленной частоты к общему чисоу наблюдений: $p_{i}^{\sum}= \frac{n_{i}^{\sum}}{n}$\n",
    "\n",
    "Условные варианты - варианты, определяемые равенством $u_{i}=\frac{x_{i}-C}{h}$Б где С - ложный ноль, h - шаг\n",
    "\n",
    "Формула контроля: $\sum_{i=1}^{k}n_{i}(u_{i}+1)^4=\sum_{i=1}^{k}n_{i}u_{i}^4+4\sum_{i=1}^{k}n_{i}u_{i}^3+6\sum_{i=1}^{k}n_{i}u_{i}^2+4\sum_{i=1}^{k}n_{i}u_{i}+n$\n",
    "\n",
    "Обычный эмпирический момент порядка r* - среднее значение r-ых степеней разностей $x_{i}-C$: $\nu_{r}^{'}=\frac{1}{n}\sum_{i=1}^{k}n_{i}(x_{i}-C)^r$\n",
    "\n",
    "Начальный эмпирический момент порядка r - обычный момент порядка r при C=0: $\nu_{r}=\frac{1}{n}\sum_{i=1}^{k}n_{i}x_{i}^{r}$\n",
    "Начальный эмпирический момент 1 порядка - выборочное среднее\n",
    "\n",
    "Центральный эмпирический момент порядка r - обычный момент r при $C=\overline{x_{B}}$: $\mu_{r}^{*}=\frac{1}{n}\sum_{i=1}^{k}n_{i}(x_{i}-\overline{x_{B}})^r$\n",
    "\n",
    "1) $\mu_{1}^{*}=0$\n",
    "\n",
    "2) $\mu_{2}^{*}=(\nu_{2}^{*}-(\nu_{1}^{*})^2)h^2$\n",
    "\n",
    "3) $\mu_{3}^{*}=(\nu_{3}^{*}-3\nu_{2}^{*}\nu_{1}^{*}+2(\nu_{1}^{*})^3)h^3$\n",
    "\n",
    "4) $\mu_{4}^{*}=(\nu_{4}^{*}-4\nu_{3}^{*}\nu_{1}^{*}+6\nu_{2}^{*}(\nu_{1}^{*})^2-3(\nu_{1}^{*})^4)h^4$\n",
    "\n",
    "Условный эмпирический момент порядка r - начальный момент порядка r, вычисленный для условных вариант: $\nu_{r}^{*}=\frac{1}{n}\sum_{i=1}^{k}n_{i}x_{i}^{r}=\frac{1}{n}\sum_{i=1}^{k}n_{i}(\frac{x_{i}-C}{h})^r$\n",
    "\n",
    "Выборочное среднее - среднее арифметическое значений признака выборочной совокупности: $\overline{x_{B}}=\frac{1}{n}\sum_{i=1}^{n}x_{i}=\sum_{i=1}^{k}\frac{x_{i}n_{i}}{n}=\sum_{i=1}^{k}x_{i}p_{i}^{*}$\n",
    "\n",
    "Выборочная дисперсия - среднее арифметическое квадратов отклонений наблюдаемых значений признака от из средних значений $\overline{x_{B}}$ : $\sigma_{B}^{2}=\frac{1}{n}\sum_{i=1}^{n}(x_{i}-\overline{x_{B}})^2=\sum_{i=1}^{k}\frac{(x_{i}-\overline{x_{B}})^2n_{i}}{n}=\sum_{i=1}^{k}(x_{i}-\overline{x_{B}})^2p_{i}^{*}$\n",
    "\n",
    "Выборочное СКО*: $\sigma_{B}=\sqrt{\sigma_{B}^{2}}$\n",
    "\n",
    "Исправленная выборочная дисперсия: $s^2=\frac{n}{n-1}\sigma_{B}^{2}$. \n",
    "\n",
    "Исправленное СКО: $s=\sqrt{s^2}$\n",
    "\n",
    "Коэффициент ассиметрии: $a_{s}^{*}=\frac{\mu_{3}^{8}}{\sigma_{B}^{3}}$\n",
    "\n",
    "Коэффициент экцесса: $\varepsilon_{k}^{*}=\frac{\mu_{4}^{*}}{\sigma_{B}^{4}}-3$\n",
    "\n",
    "Мода вариационного ряда - такое значение варианты, которой соответствует наибольшая частота. \n",
    "\n",
    "Мода $M_{o}^{*}$ интервального ряда - число, заключённое в частичном интервале, которому соответсвует наибольшая частота. $M_{o}^{*}=x_{M_{o}}^{(0)}+h\frac{n_{M_{o}}-n_{M_{o}-1}}{(n_{M_{o}}-n_{M_{o}-1})+(n_{M_{o}}-n_{M_{o}+1})}$, где $n_{M_{o}}$ - частота, модального интервала, $n_{M_{o}-1}$ - частота, соответствующая предыдущему интервалу, $n_{M_{o}+1}$ - частота, соответствующая следующему интервалу, $x_{M_{o}}^{(0)}$ - варианта, соответствующая среднему значению интервала наибольшей частоты\n",
    "\n",
    "Медиана вариационного ряда - значение признака, приходящееся на середину ранжированного ряда наблюдений. \n",
    "\n",
    "Медиана $M_{e}^{*}$интервального ряд - число, принадлежащее частичному интервалу, для которого накопленная частота состовляет половину или больше половины всей суммы частот, а предыдущая накопленная частота меньше половины всей суммы частот. $M_{e}^{*}=x_{M_{e}}^{(0)}+\frac{h}{p_{M_{e}}^{*}}(0,5 - p\sum_{M_{e}-1})$, где $p_{M_{e}}^{*}$ - относительная частота медианного интервала, $p\sum_{M_{e}-1}$ - накопленная относительная частота, соответствующая предыдущему частичному интервалу,  $x_{M_{e}}^{(0)}$ - варианта, соответствующая среднему значению интервала, для которого накопленная частота состовляет половину или больше половины всей суммы частот, а предыдущая накопленная частота меньше половины всей суммы частот\n",
    "\n",
    "Доверительный интервал для оценки неизвестного МО при неизвестном $\sigma$, но известном объёме генеральной совокупности N и доверительной надёжности $\gamma$: $(\overline{x_{B}}-\frac{t_{\gamma}s}{\sqrt{n}}\sqrt{1-\frac{n}{N}};\overline{x_{B}}+\frac{t_{\gamma}s}{\sqrt{n}}\sqrt{1-\frac{n}{N}})$\n",
    "\n",
    "Доверительный интервал для оценки генерального СКО $\sigma$ с заданной надёжностью:\n",
    "$s(1-q)<\sigma<s(1+q)$, если q<1,\n",
    "$0<\sigma<s(1+q)$, если q>1     \n",
    "\n",
    "Статистическая гипотеза - любое предположение о генеральной совокупности, проверяемое по выборке.\n",
    "\n",
    "Теоретические частоты - частоты, которые находятся по формуле $n_{i}^{'}=np_{i}$, где n - объём выборки,$p_{i}$ - точечная вероятность варианты $x_{i}$ дискретной случайной величины или интервальная вероятность для варианты $x\in(x_{i-1};x_{i})$ непрерывной случайной величины.\n",
    "\n",
    "$\chi_{nab}^{2}=\sum_{i=1}^{k}\frac{(n_{i}-n_{i}^{'})^2}{n_{i}{'}}=\sum_{i=1}^{k}\frac{n_{i}^{2}}{n_{i}^{'}}-n$\n",
    "\n",
    "$\chi_{kr}^{2}=\chi^{2}(\alpha, df)$, где $\alpha$ - заданный уровень значимости, $df=k-r-1$ - число степеней свободы, где k - число частичных интервалов выборки, r -  число параметров дифференциальной функции распределения.\n",
    "\n",
   ]
  },
  {
   "cell_type": "markdown",
   "id": "fc6682f6",
   "metadata": {},
   "source": [
    "## Постановка задачи\n",
    "Осуществить формирование репрезентативной выборки заданного объема из имеющейся генеральной совокупности экспериментальных данных.\n",
    "Осуществить последовательное преобразование полученной выборки в\n",
    "ранжированный, вариационный и интервальный ряды. Применительно\n",
    "к интервальному ряду построить и отобразить графически полигон, гистограмму и эмпирическую функцию распределения для абсолютных и\n",
    "относительных частот. Для заданных выборочных данных вычислить с\n",
    "использованием метода моментов и условных вариант точечные статистические оценки математического ожидания, дисперсии, среднеквадратичного отклонения, асимметрии, эксцесса, моды, медианы и коэффициента вариации исследуемой случайной величины. Для заданной надёжности определить границы доверительных интервалов для матема1\n",
    "тического ожидания и среднеквадратичного отклонения случайной величины. Проверить гипотезу о нормальном распределении исследуемой\n",
    "случайной величины с помощью критерия Пирсона 𝜒\n",
    "2\n",
    ". Полученные результаты содержательно проинтерпретировать.\n"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "b0aaf788",
   "metadata": {},
   "source": [
    "## Выполнение работы"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "73c5dffd",
   "metadata": {},
   "source": [
    "## Задание 1\n",
    "Из генеральной совокупности сформировать выборку заданного объёма в соответствии с полученным от преподавателя номером. Указать, какого вида выборка получилась.\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 23,
   "id": "b36fcfeb",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Выборка объемом 101 элемент, выборка серийная\n"
     ]
    }
   ],
   "source": [
    "import numpy as np\n",
    "import matplotlib.pyplot as plt\n",
    "from scipy.stats import laplace\n",
    "import pandas as pd\n",
    "from sympy import *\n",
    "import math\n",
    "import seaborn as sns\n",
    "\n",
    "\n",
    "\n",
    "X = [75,55,65,50,90,75,60,65,80,75,62,45,50,49,82,87,45,70,48,65,65,68,53,75,80,95,70,58,82,94,85,50,50,65,69,90,60,60,70,72,51,80,57,68,53,60,70,95,70,60,49,72,45,50,55,45,45,60,42,72,41,58,85,69,70,42,55,70,67,60,79,59,51,65,44,57,60,42,58,63,63,55,53,52,45,53,55,62,65,61,56,40,44,51,67,42,70,55,65,90,60]\n",
    "print(\"Из генеральной совкупности (прогнозирование сердечной недостаточнности) сформирована выборка двумерная с заданным объемом (101 элемент), выборка серийная. Использоваться будет один столбец выборки (Процент крови, покидающей сердце при каждом сокращении)\")\n"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "1893bec3",
   "metadata": {},
   "source": [
    "## Задание 2\n",
    "Последовательно преобразовать выборку в ранжированный, вариационный и интервальный ряды. Результаты содержательно проинтерпретировать.\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 24,
   "id": "77cfe2ba",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Ранжированный ряд [40, 41, 42, 42, 42, 42, 44, 44, 45, 45, 45, 45, 45, 45, 48, 49, 49, 50, 50, 50, 50, 50, 51, 51, 51, 52, 53, 53, 53, 53, 55, 55, 55, 55, 55, 55, 56, 57, 57, 58, 58, 58, 59, 60, 60, 60, 60, 60, 60, 60, 60, 60, 61, 62, 62, 63, 63, 65, 65, 65, 65, 65, 65, 65, 65, 67, 67, 68, 68, 69, 69, 70, 70, 70, 70, 70, 70, 70, 70, 72, 72, 72, 75, 75, 75, 75, 79, 80, 80, 80, 82, 82, 85, 85, 87, 90, 90, 90, 94, 95, 95]\n",
      "Вариационный ряд {40: 1, 41: 1, 42: 4, 44: 2, 45: 6, 48: 1, 49: 2, 50: 5, 51: 3, 52: 1, 53: 4, 55: 6, 56: 1, 57: 2, 58: 3, 59: 1, 60: 9, 61: 1, 62: 2, 63: 2, 65: 8, 67: 2, 68: 2, 69: 2, 70: 8, 72: 3, 75: 4, 79: 1, 80: 3, 82: 2, 85: 2, 87: 1, 90: 3, 94: 1, 95: 2}\n",
      "           x_inter  n_i    x_i       p_i\n",
      "0  (39.999, 47.86]   14  43.93  0.138614\n",
      "1   (47.86, 55.72]   22  51.79  0.217822\n",
      "2   (55.72, 63.58]   21  59.65  0.207921\n",
      "3   (63.58, 71.44]   22  67.51  0.217822\n",
      "4    (71.44, 79.3]    8  75.37  0.079208\n",
      "5    (79.3, 87.16]    8  83.23  0.079208\n",
      "6    (87.16, 95.0]    6  91.08  0.059406\n"
     ]
    }
   ],
   "source": [
    "\n",
    "x_ran = sorted(X)\n",
    "print('Ранжированный ряд', x_ran)\n",
    "\n",
    "x_var = {}\n",
    "for i in x_ran:\n",
    "    if i not in x_var:\n",
    "        x_var[i] = 1\n",
    "    else:\n",
    "        x_var[i] += 1\n",
    "print(\"Вариационный ряд\", x_var)\n",
    "\n",
    "R = max(X) - min(X)\n",
    "k = round(1 + math.log2(R))\n",
    "h = round(R/k, 2)\n",
    "s = pd.Series(x_ran)\n",
    "bins = np.concatenate(( np.arange(40, 95, h), [95]))\n",
    "count = pd.cut(x_ran, bins, include_lowest = True).value_counts().rename_axis('x_inter').reset_index(name='n_i')\n",
    "g = np.array(bins)\n",
    "Y = []\n",
    "for i in range(1, len(g)):\n",
    "    Y = [g[i] - ((g[i]-g[i-1])/2) for i in range(1, len(g))]\n",
    "count['x_i'] = Y\n",
    "\n",
    "count['p_i'] = count.n_i/101\n",
    "\n",
    "\n",
    "print(count)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "cb42297b",
   "metadata": {},
   "source": [
    "## Задание 3\n",
    "Для интервального ряда абсолютных частот построить и отобразить графически полигон, гистограмму и эмпирическую функцию.\n",
    "Сделать выводы."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "id": "170633ec",
   "metadata": {},
   "outputs": [
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "C:\\Users\\Admin\\anaconda3\\lib\\site-packages\\seaborn\\distributions.py:2619: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).\n",
      "  warnings.warn(msg, FutureWarning)\n"
     ]
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "\n",
    "sns.distplot(X, kde = False, bins = 7)\n",
    "plt.title('Гистограмма абсолютных частот')\n",
    "plt.xlabel('Интервал')\n",
    "plt.ylabel('n_i')\n",
    "plt.grid(True)\n",
    "plt.show()\n",
    "\n",
    "sns.lineplot(data = count, x='x_i', y='n_i')\n",
    "plt.title('Полигон абсолютных частот')\n",
    "plt.xlabel('x_i')\n",
    "plt.ylabel('n_i')\n",
    "plt.grid(True)\n",
    "plt.show()\n",
    "\n",
    "hist, p = np.histogram(X, bins=7)\n",
    "X = hist.cumsum()\n",
    "for i in range(len(X)):\n",
    "    plt.plot([p[i], p[i+1]],[X[i], X[i]])\n",
    "plt.title('Абсолютная Эмпирическая функция распред')\n",
    "plt.xlabel('интервалы')\n",
    "plt.grid(True)\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "4e443562",
   "metadata": {},
   "source": [
    "Вывод: по графикам нельзя судить о распределении выборки"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "1398ebb9",
   "metadata": {},
   "source": [
    "## Задание 4\n",
    "Аналогичные действия выполнить для интервального ряда относительных частот. Сравнить результаты и сделать выводы.\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 26,
   "id": "582d2f29",
   "metadata": {
    "scrolled": true
   },
   "outputs": [
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "C:\\Users\\Admin\\anaconda3\\lib\\site-packages\\seaborn\\distributions.py:2619: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).\n",
      "  warnings.warn(msg, FutureWarning)\n"
     ]
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "\n",
    "sns.distplot(X, kde=False, norm_hist=True, bins = 7)\n",
    "plt.title('Гистограмма относительных частот')\n",
    "plt.xlabel('Интервалы')\n",
    "plt.ylabel('p_i')\n",
    "plt.grid(True)\n",
    "plt.show()\n",
    "\n",
    "sns.lineplot(data = count, x='x_i', y='p_i')\n",
    "plt.title('Полигон относительных частот')\n",
    "plt.xlabel('x_i')\n",
    "plt.ylabel('p_i')\n",
    "plt.grid(True)\n",
    "plt.show()\n",
    "\n",
    "hist, p = np.histogram(X, bins=7, weights=np.ones_like(X)/len(X))\n",
    "X = hist.cumsum()\n",
    "for i in range(len(X)):\n",
    "    plt.plot([p[i], p[i+1]],[X[i], X[i]])\n",
    "plt.title('Относительная Эмпирическая функция распред ')\n",
    "plt.xlabel('интервалы')\n",
    "plt.grid(True)\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "4da2e70a",
   "metadata": {},
   "source": [
    "Вывод: При сравнении графиков из 3 и 4 пунктов( для относитлельных и абсолютных частот), можно заметить, что графики практически не отличаются друг от друга. Различия лишь в том, какие значения идут по оси у."
   ]
  },
  {
   "cell_type": "markdown",
   "id": "70feda29",
   "metadata": {},
   "source": [
    "## Задание 5\n",
    "Для интервального ряда найти середины интервалов, а также накопленные частоты. Результаты представить в виде таблицы (в последней строке Σ необходимо записать сумму столбца):"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 27,
   "id": "4d35708e",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "           x_inter  n_i    x_i   p_i  n_nak  p_nak\n",
      "0  (39.999, 47.86]   14  43.93  0.14     14   0.14\n",
      "1   (47.86, 55.72]   22  51.79  0.22     36   0.36\n",
      "2   (55.72, 63.58]   21  59.65  0.21     57   0.56\n",
      "3   (63.58, 71.44]   22  67.51  0.22     79   0.78\n",
      "4    (71.44, 79.3]    8  75.37  0.08     87   0.86\n",
      "5    (79.3, 87.16]    8  83.23  0.08     95   0.94\n",
      "6    (87.16, 95.0]    6  91.08  0.06    101   1.00\n",
      "Sum:                101         1.0\n"
     ]
    }
   ],
   "source": [
    "\n",
    "N = []\n",
    "n0 = count.n_i[0]\n",
    "n1 = n0 + count.n_i[1]\n",
    "n2 = n1 + count.n_i[2]\n",
    "n3 = n2 + count.n_i[3]\n",
    "n4 = n3 + count.n_i[4]\n",
    "n5 = n4 + count.n_i[5]\n",
    "n6 = n5 + count.n_i[6]\n",
    "N = [n0, n1, n2, n3, n4, n5, n6]\n",
    "count['n_nak'] = N\n",
    "P = []\n",
    "p0 = count.p_i[0]\n",
    "p1 = p0 + count.p_i[1]\n",
    "p2 = p1 + count.p_i[2]\n",
    "p3 = p2 + count.p_i[3]\n",
    "p4 = p3 + count.p_i[4]\n",
    "p5 = p4 + count.p_i[5]\n",
    "p6 = p5 + count.p_i[6]\n",
    "P = [p0, p1, p2, p3, p4, p5, p6]\n",
    "count['p_nak'] = P\n",
    "count = np.round(count, 2)\n",
    "print(count)\n",
    "print('Sum:               ', sum(count.n_i), '       ', round(p6, 2))"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "8f9d20c7",
   "metadata": {},
   "source": [
    "## Задание 6\n",
    "Для полученных вариант вычислить условные варианты. Заполнить расчётную таблицу (в последней строке Σ необходимо записать сумму столбца). Проконтролировать корректность вычислений."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "id": "441d86fd",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "     x_i  n_i  u_i    un    u2n    u3n     u4n    nu14\n",
      "0  43.93   14 -3.0 -42.0  126.0 -378.0  1134.0   224.0\n",
      "1  51.79   22 -2.0 -44.0   88.0 -176.0   352.0    22.0\n",
      "2  59.65   21 -1.0 -21.0   21.0  -21.0    21.0     0.0\n",
      "3  67.51   22  0.0   0.0    0.0    0.0     0.0    22.0\n",
      "4  75.37    8  1.0   8.0    8.0    8.0     8.0   128.0\n",
      "5  83.23    8  2.0  16.0   32.0   64.0   128.0   648.0\n",
      "6  91.08    6  3.0  18.0   54.0  162.0   486.0  1536.0\n",
      "7      -  101    - -65.0  329.0 -341.0  2129.0  2580.0\n",
      "Проверили по вормуле контроля, все верно, вычисления корректны\n"
     ]
    }
   ],
   "source": [
    "\n",
    "if (k % 2) == 0:\n",
    "    if count.n_i[k/2] > count.n_i[k/2+1]:\n",
    "        c = count.x_i[k/2]\n",
    "    else:\n",
    "        c = count.x_i[k/2+1]\n",
    "else:\n",
    "    c = count.x_i[k//2]\n",
    "count['u_i'] = np.round((count.x_i - c)/h, 1)\n",
    "count['un'] = np.round(count.u_i * count.n_i, 1)\n",
    "count['u2n'] = np.round(((count.u_i)**2) * count.n_i, 1)\n",
    "count['u3n'] = np.round(((count.u_i)**3) * count.n_i, 1)\n",
    "count['u4n'] = np.round(((count.u_i)**4) * count.n_i, 1)\n",
    "count['nu14'] = count.n_i*(count.u_i+1)**4\n",
    "v='-'\n",
    "count.loc[len(count.index)]=[v, sum(count.n_i), v, round(p6, 2), v, v, v, sum(count.un), sum(count.u2n), sum(count.u3n), sum(count.u4n), sum(count.nu14)]\n",
    "\n",
    "print(count[['x_i', 'n_i', 'u_i', 'un', 'u2n', 'u3n', 'u4n', 'nu14']])\n",
    "\n",
    "if (count.nu14[7] == count.u4n[7] + 4*count.u3n[7] + 6*count.u2n[7] + 4*count.un[7] + (len(X))):\n",
    "     print('При проверке по по вормуле контроля получилось равенство, вычисления корректны')\n",
    "else:\n",
    "    print(\"Неверно, вычисления не корректны\")"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "c4948eaa",
   "metadata": {},
   "source": [
    "При проверке корректности вычислений по формуле контроля значения совпали. Вычисления корректны"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "5eb67852",
   "metadata": {},
   "source": [
    "## Задание 7\n",
    "Вычислить условные эмпирические моменты 𝜈*i через условные варианты. С помощью условных эмпирических моментов вычислить\n",
    "центральные эмпирические моменты 𝜇*𝑖. Полученные результаты занести в таблицу"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 29,
   "id": "24accf42",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "21.07\n",
      "     v_i      m_i\n",
      "0  -0.64     0.00\n",
      "1   3.26   176.10\n",
      "2  -3.38  1143.52\n",
      "3  21.07 -1900.59\n"
     ]
    }
   ],
   "source": [
    "\n",
    "v = 0\n",
    "for i in range(7):\n",
    "    v += count.n_i[i] * ((count.x_i[i] -c)/h)\n",
    "v1 = np.round((v / len(X)), 2)\n",
    "v=0\n",
    "for i in range(7):\n",
    "    v += count.n_i[i] * (((count.x_i[i] -c)/h)**2)\n",
    "v2 = np.round(v / len(X), 2)\n",
    "v=0\n",
    "for i in range(7):\n",
    "    v += count.n_i[i] * (((count.x_i[i] -c)/h)**3)\n",
    "v3 = np.round(v / len(X), 2)\n",
    "v=0\n",
    "for i in range(7):\n",
    "    v += count.n_i[i] * (((count.x_i[i] -c)/h)**4)\n",
    "v4 = np.round(v / len(X), 2)\n",
    "print(v4)\n",
    "m1 = 0\n",
    "m2 = np.round((v2 - (v1**2)) * h**2, 2)\n",
    "m3 = np.round((v3 - 3*v2*v1 + 2*((v1)**3))*h**3, 2)\n",
    "m4 = np.round((v4 - 4*v3*v1 + 6*v2*((v1)**2))-3*((v1)**4)*h**4, 2)\n",
    "count2 = pd.DataFrame({'v_i': [v1, v2, v3, v4], 'm_i': [m1, m2, m3, m4]})\n",
    "print(count2)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "a51a4913",
   "metadata": {},
   "source": [
    "## Задание 8\n",
    "Вычислить выборочные среднее и дисперсию с помощью стандартной формулы и с помощью условных вариант. Убедиться, что результаты совпадают."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 30,
   "id": "7ce128f6",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Выборочное среднее с помощью стандартной формулы 63.0\n",
      "Выборочное среднее с помощью условных вариант 63\n",
      "Выборочная дисперсия с помощью стандартной формулы 176.0\n",
      "Выборочная дисперсия с помощью условынх вариант 176.0\n"
     ]
    }
   ],
   "source": [
    "\n",
    "x_v_sr2 = h * v1 +c\n",
    "x_v_sr = 0\n",
    "for i  in range(7):\n",
    "    x_v_sr += count.x_i[i] * count.p_i[i]\n",
    "x_v_sr1 = np.round(x_v_sr, 0)\n",
    "print('Выборочное среднее с помощью стандартной формулы', x_v_sr1)\n",
    "print('Выборочное среднее с помощью условных вариант', math.ceil(x_v_sr2))\n",
    "d = 0\n",
    "for i in range(7):\n",
    "    d += count.n_i[i] * ((count.x_i[i]-x_v_sr2)**2)\n",
    "disp1 = np.round(d/len(X), 0)\n",
    "disp2 = np.round(m2)\n",
    "print('Выборочная дисперсия с помощью стандартной формулы', disp1)\n",
    "print('Выборочная дисперсия с помощью условынх вариант', disp2)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "ea81c0a3",
   "metadata": {},
   "source": [
    "При сравнении полученные с помощью стандартных формул и с помощью условных вариант выборочное среднее и дисперсию. Результаты совпали, вычисления корректны "
   ]
  },
  {
   "cell_type": "markdown",
   "id": "f9b56a87",
   "metadata": {},
   "source": [
    "## Задание 9\n",
    "Вычислить исправленную выборочную дисперсию и исправленное СКО. Сравнить данные оценки с смещёнными оценками дисперсии и СКО."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 31,
   "id": "25adee0b",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Выборочное SKO: 13.27\n",
      "Исправленное ско: 13.33\n",
      "Выборочная дисперсия 176.0\n",
      "Исправленная дисперсия: 177.76\n"
     ]
    }
   ],
   "source": [
    "\n",
    "isp_disp = (len(X)/(len(X)-1))*disp2\n",
    "isp_sko = np.round(math.sqrt(isp_disp), 2)\n",
    "v_sko = np.round(math.sqrt(disp1), 2)\n",
    "print('Выборочное SKO:', v_sko)\n",
    "print('Исправленное ско:', isp_sko)\n",
    "print('Выборочная дисперсия', disp1)\n",
    "print('Исправленная дисперсия:',isp_disp)\n"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "8881b832",
   "metadata": {},
   "source": [
    "Показатели выборочного ско и дисперсии практически равны показателям исправленного ско и дисперсии, т.к. выборка имеет большой объем"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "bdb0bb1a",
   "metadata": {},
   "source": [
    "## Задание 10\n",
    "Найти статистическую оценку коэффициентов асимметрии и эксцесса. Сделать выводы"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 32,
   "id": "63584f0c",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Коэффициент ассиметрии 0.489\n",
      "Коэффициент эксцесса -0.061\n"
     ]
    }
   ],
   "source": [
    "\n",
    "a_s = np.round(m3/(v_sko**3), 3)\n",
    "e_k = np.round(m4/(v_sko**4), 3)\n",
    "print('Коэф ассиметрии', a_s)\n",
    "print('Коэф эксцесса', e_k)\n"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "889e32b1",
   "metadata": {},
   "source": [
    "Вывод:Коэф ассиметрии больше 0, занчит кривая распределения более полога справа. Коэф эксцесса отрицательный, значит кривая распределения плосковершинна"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "9d4858f7",
   "metadata": {},
   "source": [
    "## Задание 11\n",
    "Вычислить моду, медиану и коэффициент вариации для заданного\n",
    "распределения. Сделать выводы."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 33,
   "id": "d7395b4c",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Moda: 64.104\n",
      "Mediana: 60.96\n",
      "Кoэффициент вариации: 21.06 %\n"
     ]
    }
   ],
   "source": [
    "\n",
    "c = 0\n",
    "for i in range(6):\n",
    "    if count.n_i[i]>=c:\n",
    "        c = count.n_i[i]\n",
    "        b = i\n",
    "Moda = g[b] + h*((count.n_i[b]-count.n_i[b-1])/((count.n_i[b]-count.n_i[b-1])+(count.n_i[b]-count.n_i[b+1])))\n",
    "print(\"Moda:\", Moda)\n",
    "c = 0\n",
    "for i in range(6):\n",
    "    c += count.p_i[i]\n",
    "    if c >= ((sum(count.p_i))/4):\n",
    "        b = i\n",
    "        break\n",
    "Med = g[b] + (h/count.p_i[b])*(0.5 - count.p_nak[b-1])\n",
    "Med = round(Med, 2)\n",
    "print('Mediana:', Med)\n",
    "k_var = (math.sqrt(disp1)/abs(x_v_sr1)) *100\n",
    "k_var = np.round(k_var, 2)\n",
    "print('Кoэф вариации:', k_var, \"%\")"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "f9d8a8e0",
   "metadata": {},
   "source": [
    "Вывод: Мода в интервальном ряду - центральное значение модального интервала (имеющего наибольшую частоту)\n",
    "По обе стороны от медианы находится одинаковое количество единиц совокупности.\n",
    "Коэффициент вариации - стандартная мера дисперсии распределения вероятностей или частотного распределения. Позволяет сравнивать вариабельность признаков, имеющих разные единицы измерения. Позволяет судить об однородности совокупности. В данном случаей он равен 21,06%, находиться в диапазоне 17-33%, значит совокупность достаточно однородная."
   ]
  },
  {
   "cell_type": "markdown",
   "id": "8f40b6e7",
   "metadata": {},
   "source": [
    "## Задание 12\n",
    "Вычислить точность и доверительный интервал для математического ожидания при неизвестном среднеквадратичном отклонении\n",
    "при заданном объёме выборки для доверительной точности 𝛾 ∈ {0.95, 0.99}. Сделать выводы."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 34,
   "id": "86cee9a4",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Доверит интервал для мат ожидания при надежности 0,95: (60.0; 66.0)\n",
      "Доверит интервал для мат ожидания при надежности 0,99: (60.0; 66.0)\n"
     ]
    }
   ],
   "source": [
    "\n",
    "l1 = 0.95\n",
    "l2 = 0.99\n",
    "t_l1 = 1.98\n",
    "t_l2 = 2.63\n",
    "d_i_1_0 = np.round(x_v_sr1 - ((t_l1*isp_sko)/math.sqrt(len(X))), 3)\n",
    "d_i_1_1 = np.round(x_v_sr1 + ((t_l1*isp_sko)/math.sqrt(len(X))), 3)\n",
    "d_i_2_0 = np.round(x_v_sr1 - ((t_l2*isp_sko)/math.sqrt(len(X))), 3)\n",
    "d_i_2_1 = np.round(x_v_sr1 + ((t_l2*isp_sko)/math.sqrt(len(X))), 3)\n",
    "print('Доверительный интервал для мат ожидания при надежности 0,95: (', d_i_1_0, '; ', d_i_1_1, ')', sep=\"\")\n",
    "print('Доверительный интервал для мат ожидания при надежности 0,99: (', d_i_2_0, '; ', d_i_2_1, ')', sep=\"\")"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "0854207a",
   "metadata": {},
   "source": [
    "Вывод:При заданных значениях доверительной точности найдены два доверительных интервала для мат ожидания, в которые и будет попадат значение мат ожидания"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "b0f4d221",
   "metadata": {},
   "source": [
    "## Задание 13\n",
    "Для вычисления границ доверительного интервала для среднеквадратичного отклонения определить значение 𝑞 при заданных 𝛾 и 𝑛.\n",
    "Построить доверительные интервалы, сделать выводы."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 35,
   "id": "840becb5",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Доверит интервал для SKO при надежности 0,95: (11.0; 15.0)\n",
      "Доверит интервал для SKO при надежности 0,99: (11.0; 16.0)\n"
     ]
    }
   ],
   "source": [
    "\n",
    "q1 = 0.143\n",
    "q2 = 0.198\n",
    "di3_0 = np.round(isp_sko*(1-q1), 3)\n",
    "di3_1 = np.round(isp_sko*(1+q1), 3)\n",
    "di4_0 = np.round(isp_sko*(1-q2), 3)\n",
    "di4_1 = np.round(isp_sko*(1+q2), 3)\n",
    "print('Доверительный интервал для SKO при надежности 0,95: (', di3_0, '; ', di3_1, ')', sep=\"\")\n",
    "print('Доверительный интервал для SKO при надежности 0,99: (', di4_0, '; ', di4_1, ')', sep=\"\")"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "66234f17",
   "metadata": {},
   "source": [
    "Вывод: При заданных значениях доверительной точности найдены два доверительных интервала для ско, в которые и будет попадат значение ско"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "3e54b3a6",
   "metadata": {},
   "source": [
    "## Задание 14\n",
    " Проверить гипотезу о нормальности заданного распределения с помощью критерия 𝜒2 (Пирсона). Для этого необходимо найти теоретические частоты и вычислить наблюдаемое значение критерия. Для удобства вычисления необходимо заполнить расчётную таблицу (в последней строке Σ необходимо записать сумму столбца).Проконтролировать корректность вычисления 𝜒2 набл. Далее по заданному уровню значимости 𝛼 = 0.05 и числу степеней свободы 𝑑𝑓 найти критическую точку 𝜒2крит и сравнить с наблюдаемым значением. Сделать выводы."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 36,
   "id": "c1945829",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "           x_inter  n_i   p_in      nii    n_i_nii  n_i_nii_nii  ni2  ni2_nii\n",
      "0  (39.999, 47.86]   14  0.166   16.766   7.650756        0.456  196   11.690\n",
      "1   (47.86, 55.72]   22  0.134   13.534  71.673156        5.296  484   35.762\n",
      "2   (55.72, 63.58]   21  0.239   24.139   9.853321        0.408  441   18.269\n",
      "3   (63.58, 71.44]   22  0.206   20.806   1.425636        0.069  484   23.263\n",
      "4    (71.44, 79.3]    8  0.114   11.514  12.348196        1.072   64    5.558\n",
      "5    (79.3, 87.16]    8  0.063    6.363   2.679769        0.421   64   10.058\n",
      "6    (87.16, 95.0]    6  0.078    7.878   3.526884        0.448   36    4.570\n",
      "7            сумма  101  1.000  101.000          -        8.170    -  109.170\n",
      "X**2 критическое: 9.49\n",
      "Х**2 наблюдаемое: 8.17\n"
     ]
    }
   ],
   "source": [
    "\n",
    "s = pd.Series(x_ran)\n",
    "bins = np.concatenate(( np.arange(40, 95, h), [95]))\n",
    "tab = pd.cut(x_ran, bins, include_lowest = True).value_counts().rename_axis('x_inter').reset_index(name='n')\n",
    "g = np.array(bins)\n",
    "p_i1 = np.round(laplace.cdf((g[1]-x_v_sr2)/v_sko)-0, 3)\n",
    "p_i2 = np.round(laplace.cdf((g[2]-x_v_sr2)/v_sko)-laplace.cdf((g[1]-x_v_sr2)/v_sko), 3)\n",
    "p_i3 = np.round(laplace.cdf((g[3]-x_v_sr2)/v_sko)-laplace.cdf((g[2]-x_v_sr2)/v_sko), 3)\n",
    "p_i4 = np.round(laplace.cdf((g[4]-x_v_sr2)/v_sko)-laplace.cdf((g[3]-x_v_sr2)/v_sko), 3)\n",
    "p_i5 = np.round(laplace.cdf((g[5]-x_v_sr2)/v_sko)-laplace.cdf((g[4]-x_v_sr2)/v_sko), 3)\n",
    "p_i6 = np.round(laplace.cdf((g[6]-x_v_sr2)/v_sko)-laplace.cdf((g[5]-x_v_sr2)/v_sko), 3)\n",
    "p_i7 = np.round(1-laplace.cdf((g[6]-x_v_sr2)/v_sko), 3)\n",
    "P_i = [p_i1, p_i2, p_i3, p_i4, p_i5, p_i6, p_i7]\n",
    "tab['p_i'] = P_i\n",
    "tab['ni'] = tab['p_i'] * len(X)\n",
    "tab['(n-ni)**2'] = (tab['n'] - tab['ni'])**2\n",
    "tab['((n-ni)**2/ni)'] = tab['(n-ni)**2']/tab['ni']\n",
    "tab['n**2'] = tab['n']**2\n",
    "tab['((n)**2/ni)'] = tab['n**2']/tab['ni']\n",
    "z = '-'\n",
    "tab.loc[len(tab.index)] = ['сумма', sum(tab.n), sum(tab.p_i), sum(tab.ni), z, sum(tab['((n-ni)**2/ni)']), z, sum(tab['((n)**2/ni)'])]\n",
    "tab = np.round(tab, 3)\n",
    "print(tab)\n",
    "df = 7 - 2 - 1\n",
    "a = 0.05\n",
    "X2_kr = 9.49\n",
    "print('X**2 критическое:', X2_kr)\n",
    "print('Х**2 наблюдаемое:', tab.n_i_nii_nii[7])\n",
    "print('Второй способ нахождения Х**2 наблюдаемое = ', np.round(tab['((n)**2/ni)'][7] - 101, 2), 'значения совпали')\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "408b5604",
   "metadata": {},
   "source": [
    "Вывод: Наблюдаемое Х меньше, чем критическое Х, значит мы можем принять данную гипотезу о нормальном законе"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "55cf4563",
   "metadata": {},
   "source": [
    "## Выводы\n",
    "В ходе практической работы прошло ознакомление с основными правилами формирования выборки и подготовки выборочных данных к статистическому анализу, получение практических навыков нахождения точечных статистических оценок параметров распределения, а также вычисления интервальных статистических оценок параметров распределения выборочных данных и проверки «справедливости» статистических гипотез."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "37ad145b",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.9.12"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}

