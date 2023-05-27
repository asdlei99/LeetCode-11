2659.Make-Array-Empty

假设一个序列里面前三个最小的元素是x,y,z，他们在序列中的位置如下：`***x****z****y*****`

首先我们必然会x，它是第一个会被消除的元素，那么在x之前的元素我们都会挪动到最后。所以操作的次数是x之前的元素的个数。

其次我们需要消除y，那么所有在x与y之间的元素都会被挪动到最后。所需要的操作次数也就是x与y之间的元素的个数。

接着我们需要消除z。注意在上一步之后，所有在y之前的元素都已经被挪到最后去了。想要消除z，必须先挪动从y+1到z-1之间的元素，其实是一个wrap around的过程。从原始序列上看，因为z的位置在y的前面，那么我们需要挪动的元素其实包含了[y+1,n-1]以及[0:z-1]两部分。特别注意，我们要扣除掉x，因为它已经被消除了。

所以这就提示我们可以用线段树或者BIT，支持任意单个元素的删减操作，并可以高效求出任意一段区间内的剩余元素个数。