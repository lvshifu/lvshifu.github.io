---
title: Java笔记2--使用Apache Common进行通用排序
date: 2009-10-22 21:18:02
tags: [Java]
categories: 
toc: false
---

{% codeblock lang:java %}

import java.util.*;
import org.apache.commons.collections.comparators.ComparatorChain;

public class Sort
{
    public static final boolean ASC = false;
    public static final boolean DESC = true;
    private Object targetBean[];
    private List targetBeanList;
    private List sortKey;
    private List sortType;
    private ComparatorChain comparetor;

    private Sort()
    {
        targetBean = null;
        targetBeanList = null;
        sortKey = null;
        sortType = null;
        comparetor = null;
        comparetor = new ComparatorChain();
        sortKey = new ArrayList();
        sortType = new ArrayList();
    }

    public static Sort targetBean(Object beans[])
    {
        Sort sort = new Sort();
        sort.targetBean = beans;
        return sort;
    }

    public static Sort targetBean(List beansList)
    {
        Sort sort = new Sort();
        sort.targetBeanList = beansList;
        return sort;
    }

    public Sort key(String keyPropertyName, boolean sortOrder)
    {
        Boolean order = new Boolean(sortOrder);
        sortKey.add(keyPropertyName);
        sortType.add(order);
        return this;
    }

    public Object[] beans()
    {
        if(targetBeanList != null)
            listToBeans();
        execute();
        return targetBean;
    }

    public List list()
    {
        if(targetBeanList != null)
            listToBeans();
        execute();
        int len = targetBean.length;
        targetBeanList = new ArrayList();
        for(int beanIdx = 0; beanIdx < len; beanIdx++)
            targetBeanList.add(targetBean[beanIdx]);

        return targetBeanList;
    }

    private void listToBeans()
    {
        targetBean = new Object[targetBeanList.size()];
        for(int listIdx = 0; listIdx < targetBean.length; listIdx++)
            targetBean[listIdx] = targetBeanList.get(listIdx);

    }

    private void execute()
    {
        for(int idx = 0; idx < sortKey.size(); idx++)
        {
            Comparator sortComp = new SortCreateComparator((String)sortKey.get(idx));
            comparetor.addComparator(sortComp, ((Boolean)sortType.get(idx)).booleanValue());
        }

        Arrays.sort(targetBean, comparetor);
    }

}

{% endcodeblock %}

{% codeblock lang:java %}

import java.util.Comparator;
import org.apache.commons.beanutils.PropertyUtils;
import org.apache.commons.collections.comparators.NullComparator;

final class SortCreateComparator
    implements Comparator
{

    private String sortKey;
    private NullComparator comparetor;

    protected SortCreateComparator(String sortKey)
    {
        this.sortKey = sortKey;
        comparetor = new NullComparator(true);
    }

    public int compare(Object o1, Object o2)
        throws RuntimeException
    {
        int ret = 0;
        Object obj1 = null;
        Object obj2 = null;
        try
        {
            obj1 = PropertyUtils.getProperty(o1, sortKey);
            obj2 = PropertyUtils.getProperty(o2, sortKey);
            ret = comparetor.compare(obj1, obj2);
        }
        catch(Exception e)
        {
            throw new RuntimeException(e);
        }
        return ret;
    }

}


{% endcodeblock %}


Listに格納されたBeanや、Bean配列に格納されたBeanをソートします。
ソートを行うクラスはgetterが含まれるBeanの配列か、 そのBeanが格納されたListである必要があります。 
次にSortクラスを使用した例を説明します。 

・ソート対象Bean 

```java
public class bean { 
	private Integer id; 
	private String name; 
	public void setId(Integer i) { this.id = i; } 
	public void setName(String str) { this.name = str; } 
	public Integer getId(){ return this.id; } 
	public String getName(){ return this.name; } 
}
```

 ・ソート実行テスト 

```java
public class test { 
	public void testSort(){ 
		List beanList = new ArrayList(); 
		Bean bean = new Bean(); 
		bean.setId(new Integer(3)); 
		bean.setName("新井　武"); 
		beanList.add(bean); 
		bean = new Bean(); 
		bean.setId(new Integer(1)); 
		bean.setName("佐藤　一郎"); 
		beanList.add(bean); 
		bean = new Bean(); 
		bean.setId(new Integer(2)); 
		bean.setName("本田　幸一"); 
		beanList.add(bean); 
		beanList = Sort.targetBean(beanList).key("id", Sort.DESC).list(); 
	} 
} 
```

testSort()を実行すると、beanListには次のような値が設定されたBeanが格納されています。 

	id | name 
	---+-------------- 
	3 | 新井　武 
	2 | 本田　幸一 
	1 | 佐藤　一郎 
	
Sort#keyメソッドで指定されたキー名（プロパティ名）とソート順（昇順、降順）に従って、 Sort#listメソッドによってソートが実行されます。 
キー情報はSort#keyメソッドをいくつも指定することで、複数設定できます。 
	
	Sort.targetBean(bean).key("month", Sort.ASC) 
		.key("productName", Sort.DESC) 
		.key("price", Sort.ASC) 
		.beans(); 
	
キー情報を設定し終わりソートを実行するには、beansメソッドまたはlistメソッドを 実行します。
beansメソッドはソートされたオブジェクト配列が戻り値となり、 
listメソッドはオブジェクトが格納されたListが戻り値となります。 
