# 一、简介

在合并两个的基础上，合并一个list，用两种写法来试试

# 二、实现

```
public ListNode mergeKLists(ArrayList<ListNode> lists) {
		if (lists == null || lists.size() == 0 ) return null;
    
		ListNode dummyNode = new ListNode(-1);
		ListNode curNode = dummyNode;
		int tempIndex = 0;
		int tempVal = lists.get(0).val;
		for(int i = 1; i < lists.size(); i++){
				int val = lists.get(i).val;
				if (val < tempVal) {
						tempVal = val;
						tempIndex = i;
				}
		}
		ListNode tempNode = lists.get(tempIndex);
		curNode.next = tempNode;
		curNode = curNode.next;
		if (tempNode.next != null) {
			lists.put(tempIndex, tempNode.next)
		} else {
			lists.remove(tempIndex);
		}
		curNode.next = mergeKLists(lists);
		return dummyNode.next;
}
```

1、如果List空了，就结束了

# 三、问题列表

没有考虑到 List 里面元素为空的情况

```
for(int i = 1; i < lists.size(); i++){
				int val = lists.get(i).val;
				if (val < tempVal) {
						tempVal = val;
						tempIndex = i;
				}
		}
lists.get(i).val; // 这里空指针
```

