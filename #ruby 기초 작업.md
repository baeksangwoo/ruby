# #ruby 

rb.likelion.io에서 챗봇 만들기

### 1. 안녕

```ruby
puts "안녕하세요"
```

### 2. 코스피

```ruby
require 'httparty'
require 'nokogiri'

#원하는 정보가 있는 주소로 접근
url ='http://finance.naver.com/sise/'
#요청을 보내고 응답을 저장
res = HTTParty.get(url)
#조작하기 편하게 바꾸기
data = Nokogiri::HTML(res.body)

#바꾼 정보중에서 원하는 정보만 뽑아서
customData= data.css("#KOSPI_now")
#출력
puts customData
```

### 3 미세먼지

```ruby
require 'httparty'
url = URI.encode("http://openapi.airkorea.or.kr/openapi/services/rest/ArpltnInforInqireSvc/getMsrstnAcctoRltmMesureDnsty?stationName=강남구&dataTerm=MONTH&numOfRows=100&ServiceKey=")+key
response = HTTParty.get(url)
dust = response['response']['body']['items']['item'][0]['pm10Value'].to_i
puts dust

if (dust>150)
  puts "매우 나쁨"
  elsif (dust>80 && dust <=150)
  puts "나쁨"
  elsif(dust>30 && dust<=80)
  puts "평범"
  else
  puts "좋음"
end
```

### 4 로또

```ruby
lotto = (1...46).to_a.sample(6).sort.to_s
puts lotto
```

