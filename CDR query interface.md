# query example: #
## query number of CDR records which match the conditions: ##
"count=1" tells the server to return number of records available. This is designed for pagination. Once the client gets the number of rows, it can know the number of pages should display.

	curl -X GET 'http://localhost:8001/cdr?domain=sip.test.gelenknetworks.com&caller=%2B16478505697&callee=16473607221&start_date=2016%2d04%2d24T14%3A09%3A08.000Z&end_date=2016%2D04%2D24T14%3A10%3A08.000Z&count=1'

## query CDR records ##
	curl -X GET 'http://localhost:8001/cdr?domain=sip.test.gelenknetworks.com&page=0&page_size=10&caller=%2B16478505697&callee=16473607221&start_date=2016%2d04%2d24T14%3A09%3A08.000Z&end_date=2016%2D04%2D24T14%3A10%3A08.000Z&start_docid=8d3930ee528b8fcf8f91c7b3f1c22759'



# Parameters: #
	page  - optional, skip to a specific page. This is not recomended, please use start_docid instead.
	page_size - optional, default value is 20
	start_docid - optional, for pagination, if not exist then assume to be 1st page. Overrides page parameter.
	start_date - optional, ISO format "2016-04-29T18:58:23.000Z", must be less than end_date, default is 1970-1-1
	end_date - optional, ISO format, default is 2106-xx-xx
	domain - mandatory
	caller - phone number in E164
	callee - phone number in E164
	count - to query number of available rows, this query not return doc content. ignore start_docid

# Response example: #
	return ** 1 more ** row than requested

## query record content: ##
	{"rows":[{"_id":"8d3930ee528b8fcf8f91c7b3f1c20353","_rev":"1-1613ef66423e4d05c120b139af1501e3","answer_time":"1970-01-01T00:00:00.000Z","answersec":"0","billsec":"0","caller_id_name":"+16478505697","caller_id_number":"+16478505697","destination_number":"16473607221","direction":"inbound","end_time":"2016-04-24T14:09:08.000Z","endpoint_disposition":"RECEIVED","sip_hangup_disposition":"send_refuse","start_time":"2016-04-24T14:09:08.000Z"},
         {"_id":"8d3930ee528b8fcf8f91c7b3f1c22759","_rev":"1-95aff96fd6d63314d4db95afbd33d5ce","answer_time":"1970-01-01T00:00:00.000Z","answersec":"0","billsec":"0","caller_id_name":"+16478505697","caller_id_number":"+16478505697","destination_number":"16473607221","direction":"inbound","end_time":"2016-04-24T14:10:08.000Z","endpoint_disposition":"RECEIVED","sip_hangup_disposition":"send_refuse","start_time":"2016-04-24T14:10:08.000Z"}]}	

## query number of rows ##
	{"rows":[2]}

# pagination usage #

1. Client should query the number of available records with "count=1"
2. To query the first page of records, don't specify the "start_docid" parameter
3. server returns one more rows. For example, "page_size=10", then server returns 11 rows, if available. If returned rows less than 11, then it's the end. 
4. to query the 2nd, specify start_docid=rows[10]["_id"]
5. to jump to a specific page, use "page" parameter
