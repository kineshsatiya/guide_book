# guide_book

awesome splunk query 
index=finance-yql-prod-ats  colo=bf1 NOT widget /applewf/multiquote | fields tickers,lang,region | eval tickers=urldecode(tickers) | eval ticker=split(tickers,",") |stats count(ticker) as tcount by  ticker, region, lang |sort - tcount
