---
title: Java笔记9--Solr Word全文索引
date: 2017-05-13 16:24:03
tags: [Solr,Java]
categories: 
list_number: false
---
# Solr Word全文索引

本文使用的Solr为4.9.1版。

Solr使用apache Tika实现富文本提取，可以实现WORD、Excel、PDF等格式的处理。
<!--more-->
步骤：
# 1，Solr安装配置
网上下载solr-4.9.1.war，放入Tomcat的webapps目录下即可，启动Tomcat后，war包自动解压。

添加下列Jar文件到解包的文件夹中

    jcl-over-slf4j-1.7.6.jar
    jul-to-slf4j-1.7.6.jar
    log4j-1.2.17.jar
    slf4j-api-1.7.6.jar
    slf4j-log4j12-1.7.6.jar


# 2，新建CELL
创建solrhome。Solrhome是存放solr服务器所有配置文件的目录。
修改web.xml，配置solrhome的位置。

    <env-entry>
       <env-entry-name>solr/home</env-entry-name>
       <env-entry-value>D:\apache-tomcat-7.0.42\webapps\solr\solrhome</env-entry-value>
       <env-entry-type>java.lang.String</env-entry-type>
    </env-entry>

# 2，配置CELL


# 3，富文本提取

```java
import java.io.File;
import java.io.IOException;
import java.lang.reflect.InvocationTargetException;
import java.util.HashMap;
import java.util.Map;

import org.apache.commons.beanutils.BeanUtils;
import org.apache.solr.client.solrj.SolrQuery;
import org.apache.solr.client.solrj.SolrServer;
import org.apache.solr.client.solrj.SolrServerException;
import org.apache.solr.client.solrj.impl.HttpSolrServer;
import org.apache.solr.client.solrj.request.AbstractUpdateRequest;
import org.apache.solr.client.solrj.request.ContentStreamUpdateRequest;
import org.apache.solr.client.solrj.response.QueryResponse;
import org.dozer.DozerBeanMapper;
import org.dozer.Mapper;

import com.ces.analysis.caseinfo.entity.CaseInfo;  
  
/** 
 * 从Word创建索引 
 */  
public class SolrExampleTests  
{  
      
    public static void main(String[] args)  
    {  
        String filePath = "D:\\Projects\\20170509";   
        File root = new File(filePath);
        File[] files = root.listFiles();
        for(File dir:files){     
            if(dir.isDirectory()){
                File[] wenshues = dir.listFiles();
                    for(File wenshu:wenshues){     
                        if(wenshu.isDirectory()){
                            System.out.println("file error : " + wenshu.getAbsolutePath());
                        } else {
                            System.out.println(wenshu.getAbsolutePath());
                            System.out.println(dir.getName());
                            try  
                            {
                                // 创建索引
                                indexFilesSolrCell(wenshu.getAbsolutePath(), dir.getName()); 
                            }  
                            catch (IOException e)  
                            {  
                                e.printStackTrace();  
                            }  
                            catch (SolrServerException e)  
                            {  
                                e.printStackTrace();  
                            } 
                        }
                    }
            } else {
                System.out.println("file error : " + dir.getAbsolutePath());
            }
        }

        String urlString = "http://180.168.156.212:2113/solr/core1";  
        SolrServer solr = new HttpSolrServer(urlString);  

        try {
            String key = "text:黄酒 AND (啤酒 OR 黑啤 OR 白啤)";
            // 返回最多20000个结果
            QueryResponse rsp = solr.query(new SolrQuery(key).setRows(20000));
            SolrDocumentList list = rsp.getResults();
            System.out.println("返回：" + list.getNumFound() + "条记录\t耗时：" + rsp.getElapsedTime() + "毫秒");
            for (int i = 0; i < list.size(); i++) {
                SolrDocument doc = (SolrDocument)list.get(i);
                String objectId = doc.get("id").toString();
                //String title = doc.get("webTitle").toString();
                //String content = doc.get("webContent").toString();
                System.out.println(objectId);                
            }
        } catch (Exception e) {
            e.printStackTrace();
        } 

        System.out.println("#######################################");
    }  
      
    /** 从文件创建索引 
     * @param fileName 
     * @param solrId 
     */  
    public static void indexFilesSolrCell(String fileName, String solrId)   
        throws IOException, SolrServerException  
    {  
        // Solr服务器地址+CELL名
        String urlString = "http://localhost:8080/solr/core1";  
        SolrServer solr = new HttpSolrServer(urlString);  
        ContentStreamUpdateRequest up = new ContentStreamUpdateRequest("/update/extract");  
        
        // doc文件
        String contentType="application/msword";
        // docx文件
        //String contentType="application/vnd.openxmlformats-officedocument.wordprocessingml.document";
        up.addFile(new File(fileName), contentType);  
        up.setParam("literal.id", solrId);  
        up.setParam("uprefix", "attr_");  
        up.setParam("fmap.content", "text");  
        up.setAction(AbstractUpdateRequest.ACTION.COMMIT, true, true);  
        
        solr.request(up);  
          
        QueryResponse rsp = solr.query(new SolrQuery("*:*"));  
        System.out.println(rsp);  
    }  
      
}  

```

# 4，索引完成后即可查看效果
