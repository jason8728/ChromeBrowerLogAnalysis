# ChromeBrowerLogAnalysis
Python was used to analysis chrome brower history data:
  website visited  times; 
  visit duration;
  brower time  on  hour/date/month;


#Note on the Chrome history Database
##path
os.path.expanduser('~')+"\AppData\Local\Google\Chrome\User Data\Default

##withdraw data from Database
SELECT urls.url, urls.visit_count,visits.visit_time,visits.visit_duration FROM urls, visits WHERE urls.id = visits.url;

##warning data
1. Get the domain of website. 
  exg. get '5730.net' from 'http://www.5730.net/e/member/doaction.php'
2. Change microsecond to datetime.
  The record was about'13120364269351327', which means 3644545.63 hours ahead of '1601/01/01 00:00:00' at UTC zero zone. So in China the current time should code like this:
    df.hours=df.visit_time/10**6/60/60+8
    df.visit_time=df.hours.map(lambda x: datetime(1601,1,1)+timedelta(hours=x))

#Reference:
how to change microsecond to datetime type: http://blog.csdn.net/a809146548/article/details/51008650 
