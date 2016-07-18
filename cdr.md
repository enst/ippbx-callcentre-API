# query example: #
## query number of CDR records which match the conditions: ##
"count=1" tells the server to return number of records available. This is designed for pagination. Once the client gets the number of rows, it can know the number of pages should display.

	curl -X GET 'http://localhost:8001/cdr?domain=sip.test.gelenknetworks.com&caller=%2B16478505697&callee=16473607221&start_date=2016%2d04%2d24T14%3A09%3A08.000Z&end_date=2016%2D04%2D24T14%3A10%3A08.000Z&count=1'

## query CDR records ##
	curl -X GET 'http://localhost:8001/cdr?domain=sip.test.gelenknetworks.com&caller=%2B16478505697&callee=16473607221&start_date=2016%2d04%2d24T14%3A09%3A08.000Z&end_date=2016%2D06%2D24T14%3A10%3A08.000Z'

## query sum of call minutes ##
    curl -X GET 'http://localhost:8001/cdr?domain=sip.test.gelenknetworks.com&start_date=2016%2d04%2d24T14%3A09%3A08.000Z&end_date=2016%2D06%2D24T14%3A10%3A08.000Z&sum'

# Parameters: #
	start_date - optional, ISO format "2016-04-29T18:58:23.000Z", must be less than end_date, default is 1970-1-1
	end_date - optional, ISO format, default is 2106-xx-xx
	domain - mandatory
	caller - phone number in E164
	callee - phone number in E164
	count - to query number of available rows, this query not return doc content. ignore start_docid
	status - call status, 0:no answer, 1:answered, -1:all
	stats - to query number of available rows and sum call minutes, this query not return doc content.
	sum - sum call minutes (can only work with start_date, end_date & domain)

# Response example: #
## query record content: ##
	[{"_id":"8d3930ee528b8fcf8f91c7b3f1c20353","_rev":"1-1613ef66423e4d05c120b139af1501e3","answer_time":"1970-01-01T00:00:00.000Z","answersec":"0","billsec":"0","caller_id_name":"+16478505697","caller_id_number":"+16478505697","destination_number":"16473607221","direction":"inbound","end_time":"2016-04-24T14:09:08.000Z","endpoint_disposition":"RECEIVED","sip_hangup_disposition":"send_refuse","start_time":"2016-04-24T14:09:08.000Z"},
         {"_id":"8d3930ee528b8fcf8f91c7b3f1c22759","_rev":"1-95aff96fd6d63314d4db95afbd33d5ce","answer_time":"1970-01-01T00:00:00.000Z","answersec":"0","billsec":"0","caller_id_name":"+16478505697","caller_id_number":"+16478505697","destination_number":"16473607221","direction":"inbound","end_time":"2016-04-24T14:10:08.000Z","endpoint_disposition":"RECEIVED","sip_hangup_disposition":"send_refuse","start_time":"2016-04-24T14:10:08.000Z"}]	

## query number of rows ##
	[2]

## sum of call minutes ##
        [{"inbound":15,"outbound":4}]
        
# pagination usage #

1. Server always returns all rows match the condition, Client should perform pagination at its own side.

