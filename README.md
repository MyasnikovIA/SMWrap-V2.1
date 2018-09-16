# SMWrap-V2.1
<br><h3>www.smwrap.ru</h3>
<pre>
   1) Cache' Intersystems необходимо выключить БД "CACHELIB" из режима только чтения. 
   2) Инсталляция do $system.OBJ.Load("c:\XML\SMWrap.xml","c") 
   3) Cache' Intersystems необходимо выключить БД "CACHELIB" в режима только чтения. 
   4) Запустить сервер: do RUN^%ZMRPMD()               
</pre>

 <h3> Скрипт для инсталляции:</h3>
 <pre>
      s OldNs=$zu(5)
      d $zu(5,"%SYS")
      set db=##class(SYS.Database).%OpenId("CACHELIB")
      set db.ReadOnly=0 
      w db.%Save()
      do $system.OBJ.Load("c:\XML\SMWrap.xml","c")    ; "c:\XML\SMWrap.xml" - путь к файлу на сервере   
      set db.ReadOnly=1
      w db.%Save()
      do $zu(5,OldNs)
      do RUN^%ZMRPMD()
 </pre>
 <h3>Видеоролик для инсталляциипроекта: </h3>
https://www.youtube.com/watch?v=gy7eF1av0-8 
