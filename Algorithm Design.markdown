# Методы разработки алгоритмов

Что делать, когда вы столкнулись с новой проблемой и вам нужно найти алгоритм для ее решения.

### Это похоже на другую проблему?

Если вы можете сформулировать свою проблему с точки зрения другой, более общей проблемы, то вы, возможно, сможете использовать существующий алгоритм. Зачем изобретать велосипед?

Что мне нравится в [The Algorithm Design Manual](http://www.algorist.com) Стивена Скиены, так это то, что оно включает в себя каталог проблем и решений, которые вы можете попробовать. (См. также его [репозиторий алгоритмов](http://www3.cs.stonybrook.edu/~algorith/).)

### Можно начинать с грубой силы

Наивные решения грубой силы часто слишком медленны для практического использования, но они являются хорошей отправной точкой. Написав решение грубой силы, вы научитесь понимать, в чем на самом деле заключается проблема.

Когда у вас есть реализация грубой силы, вы можете использовать ее, чтобы убедиться, что любые улучшения, которые вы придумали, верны.

И если вы работаете только с небольшими наборами данных, то метод грубой силы сам по себе может быть достаточно хорош. Не попадайтесь в ловушку преждевременной оптимизации!

### Разделяй и властвуй

>"Когда вы меняете свой взгляд на вещи, меняется и то, на что вы смотрите".</br>
>Макс Планк, квантовый теоретик и лауреат Нобелевской премии

Разделяй и властвуй — это способ справиться с большой проблемой, разбивая ее на части и продвигаясь к решению.

Вместо того, чтобы рассматривать всю проблему как единую, огромную и сложную задачу, вы разделяете проблему на относительно более мелкие проблемы, которые легче понять и решить.

Вы решаете более мелкие проблемы и обобщаете решение, пока у вас не останется только решение. На каждом этапе проблема уменьшается, а решение становится зрелым, пока вы не получите окончательное правильное решение.

Решение меньшей задачи и повторное (или часто рекурсивное) применение одного и того же решения к другим фрагментам дает результат за меньшее время.
