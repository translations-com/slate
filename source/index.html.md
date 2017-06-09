---
title: GlobalLink Connect API Reference

language_tabs:
  - php: PHP
  - ruby: Ruby
  - python: Python

toc_footers:
  - <a href='http://www.translations.com/globallink/demo.html'>Free consultation</a>
  - <a href='http://www.translations.com/globallink/contact.html'>Contact Us!</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:


search: true
---



# GLExchange - Main Class

```php
<?php
class GLExchange
	private $pdConfig; // PDConfig
	private $submission; // Submission
	private $projectService;
	private $userProfileService;
	private $targetService;
	private $documentService;
	private $submissionService;
	private $workflowService;
	function GLExchange($connectionConfig) 
	private function _setConnectionConfig($connectionConfig)
	private function _convertTargetsToInternal($targets)
	private function _createSubmissionInfo()
	private function _createWorkflowRequest($submissionWorkflowInfo)
	private function _validateDocument($document)
	private function _validateSubmission($submission)
	function downloadTranslationKit($submissionWorkflowInfo)
	function getProject($projectShortCode)
	function getProjects()
	function getSubmissionTicket()
	function getSubmissionName($submissionTicket)
	function cancelTargetByDocumentTicket($documentTicket, $locale)
	function cancelTarget($targetTicket)
	function cancelSubmission($submissionTicket, $comment = NULL)
	function downloadTarget($ticket)
	function findAvailableWorkflowInfosForClaim($limit)
	function findAvailableWorkflowInfosForDownload($limit)
	function getCancelledTargetsBySubmission($submissionTickets, $maxResults)
	function getCancelledTargets($maxResults)
	function getCompletedTargetsByProject($project, $maxResults)
	function getCompletedTargets($maxResults)
	function getCompletedTargetsBySubmission($submissionTickets, $maxResults)
	function getPreliminaryTargets($submissionWorkflowInfo)
	function getUnstartedSubmissions($project)
	function initSubmission($submission)
	function isSubmitterValid($shortCode, $newSubmitter)
	function sendDownloadConfirmation($ticket)
	function startSubmission()
	function uploadReference($referenceDocument)
	function uploadTranslatable($document)
	function uploadTranslationKit($fileName, $data)
}
?>
```

```ruby
class GLExchange
	@connectionConfig
	@submission
	
	@documentService
	@projectService
	@submissionService
	@targetService
	@userProfileService
	@workflowService
	
	def initialize(config)
		setConnectionConfig(config)
	end
	def cancelDocument (documentTicket, locale = nil)
	end
	def cancelSubmission (submissionTicket, comment = nil)
	end
	def downloadTarget (ticket)
	end
	def getCancelledTargets (maxResults)
	end
	def getCancelledTargetsBySubmission(submissionTicket, maxResults)
	end
	def getCompletedTargets (maxResults)
	end
	def getCompletedTargetsByProject (project, maxResults )
	end
	def getCompletedTargetsByDocuments (documentTickets, maxResults )
	end
	def getCompletedTargetsBySubmission(submissionTicket, maxResults)
	end
	def getProject(shortCode)
	end
	def getProjects
	end
	def getSubmissionName (submissionTicket)
	end
	def getSubmissionTicket
	end
	def getUnstartedSubmissions (project)
	end
	def initSubmission(submission)
	end
	def isSubmitterValid(shortCode, submitter)
	end
	def sendDownloadConfirmation (ticket)
	end
	def startSubmission
	end
	def uploadReference (referenceDocument)
	end
	def uploadTranslatable (document)
	end
	def createSubmissionInfo
	end
	def validateDocument (document)
	end
	def validateSubmission (submission)
	end
	def addHeaders (obj)
	end
	def setConnectionConfig(config = nil)
	end
end
```

```python
class GLExchange:
	def __init__(self, config):
	def setConnectionConfig(self, config):
	def __setHeaders(self):
	def __createSubmissionInfo(self):
	def __getDocumentInfo(self, document):
	def __getDocumentTargetInfos (self, document):
	def __getDocumentResourceInfo(self, document):
	def __validateDocument (self, document):
	def __validateSubmission (self, submission):
	def cancelDocument (self, documentTicket, locale = None):
	def cancelSubmission (self, submissionTicket, comment = None):
	def downloadTarget (self, ticket):
	def getCancelledTargets (self, maxResults):
	def getCancelledTargetsBySubmission(self, submissionTicket, maxResults):
	def getCompletedTargets (self, maxResults):
	def getCompletedTargetsByProject (self, project, maxResults ):
	def getCompletedTargetsBySubmission(self, submissionTicket, maxResults):
	def getProject(self, shortCode):
	def getProjects(self, includeSubProjects):
	def getSubmissionName (self, submissionTicket):
	def getSubmissionTicket(self):
	def getUnstartedSubmissions (self, project):
	def initSubmission(self, submission):
	def isSubmitterValid(self, shortCode, submitter):
	def sendDownloadConfirmation (self, ticket):
	def startSubmission(self):
	def uploadReference (self, referenceDocument):
	def uploadTranslatable(self, document):
```

This is the main API class. It will initialize a connection to Project Director. Different methods are available to perform the necessary operations: 

Method | Returns | Sumary 
------ | ------- | -------
`getCancelledTargets` | Array | Get cancelled targets for all projects or Get cancelled targets for a submission
`getCompletedTargets` | Array | Get completed targets for all projects or Get completed targets for specified project or Get completed targets for submission
`getCompletedTargetsByDocuments` | Array | Get completed targets by document tickets
`getProject` | String | Get project by it`s shortcode
`getProjects` | Array | Get all user projects
`getSubmissionName` | String | Get Submission name for specified ticket
`getSubmissionTickets` | String | Get Submission ticket if a submission has been initialized
`getUnstartedSubmissions` | Array | Get Unstarted Submissions
`getSubmissionStatus` | Boolean | Get Submission status for specified ticket. True if submission is complete.
`isSubmissionComplete` | Boolean | Get Submission status for specified ticket. True if submission is complete
`startSubmission` | String | Start Submission

Method | Parmeter | Sumary 
------ | ------- | -------
`cancelDocument` | `documentTicket` | Cancel document for all languages or Cancel document for specified target language
`cancelSubmission` | `submissionTicket` | Cancel Submission for all languages or Cancel Submission for all languages with comment
`downloadCompletedTarget` | `maxResults` | Download all completed targets and returns `targetTicket`
`sendDownloadConfirmation` | `targetTicket` | Sends confirmation that the target resources was downloaded successfully by the customer
`initSubmission` | `submission` | Initialize a new Submission where `submission` object contains the PD submission configuration
`uploadReference` | `referenceDocument` | Upload reference file for submission
`uploadTranslatable` | `document` | Uploads the document to project director for translation and returns `documentTicket`
`uploadTranslationKit` | `fileName` & `data` | Uploads preliminary delivery file to project director

# Models Classes

## Project

```php
<?php
class PDProject {
	public $shortcode;
	public $name;
	public $ticket;
	public $languageDirections = array ();
	public $fileFormats = array ();
	public $workflows = array ();
	public $customAttributes = array ();
	function PDProject($externalProject)
}
?>
```

```ruby
class PDProject

	attr_accessor :shortCode
	attr_accessor :name
	attr_accessor :ticket
	attr_accessor :languageDirections
	attr_accessor :fileFormats
	attr_accessor :workflows
	attr_accessor :customAttributes

	def initialize(externalProject)
		@name = externalProject.projectInfo.name;
		@shortCode = externalProject.projectInfo.shortCode;
		@ticket = externalProject.ticket
		@languageDirections = Array.new
		@fileFormats = Array.new
		@workflows = Array.new
		@customAttributes = Array.new
	end
```

```python
class PDProject:
	shortCode = ''
	name = ''
	ticket = ''
	languageDirections = []
	fileFormats = []
	workflows = []
	customAttributes = []
```

Method | Returns | Sumary 
------ | ------- | -------
`getShortcode` | String | Get the Project Short Code in PD
`getName` | String | Get the Project Name in PD
`getTicket` | String | Project ticket, an internal ID required for creating submissions
`getLanguageDirections` | Array | Gets the list of language directions configured for the project
`getFileFormats` | Array | Gets the list of File Formats configured for the project
`getWorkflows` | Array | Gets the list of Workflows configured for the project
`getCustomAttributes` | Array | Gets the list of configured attributes for the project

## Submission

```php
<?php
class PDSubmission {
	public $customAttributes;
	public $dueDate;
	public $instructions;
	public $isUrgent;
	public $metadata;
	public $name;
	public $project;
	public $pmNotes;
	public $submitter;
	public $ticket;
	public $workflow;
}
?>
```

```ruby
class PDSubmission
	attr_accessor :customAttributes
	attr_accessor :dueDate
	attr_accessor :instructions
	attr_accessor :isUrgent
	attr_accessor :metadata
	attr_accessor :name
	attr_accessor :project
	attr_accessor :pmNotes
	attr_accessor :submitter
	attr_accessor :ticket
	attr_accessor :workflow
end
```

```python
class PDSubmission:
	customAttributes = []
	dueDate = ''
	instructions = ''
	isUrgent = False
	metadata = {}
	name = ''
	project = None
	pmNotes = ''
	submitter = ''
	ticket = ''
	workflow = None
```

Method | Returns | Sumary 
------ | ------- | -------
`getDueDate` | Date | Returns due date of submission
`getInstructions` | String | Returns submission instructions
`getMetadata` | Hash | Returns submission metadata
`getName` | String | Returns submission name
`getPmNotes` | String | Returns submission PM notes
`getProject` | String | Returns the project shortcode in which the submission was created
`getSubmitter` | String | Returns submission submitter
`isUrgent` | Boolean | Returns if submission is urgent or not. True if submission was set as urgent.

Method | Parmeter | Sumary 
------ | ------- | -------
`setCustomAttributes` | `customAttribute` | *Optional* - Set custom attributes. 
`setDueDate` | `dueDate` | *Optional* - Due date by when the submission should be completed in Project Director. This should always be greater than current date. If due date is not specified, Project Director will rely on the configured language model to calculate a due date
`setInstructions` | `Instructions` | *Optional* - Set instructions for the translators
`setMetadata` | `metadata` | *Optional* - Key-value pair of metadata, metadata is not readable in PD UI although Custom attributes are.
`setName` | `name` | Name of the submission that will show up in Project Director
`setOwner` | `owner` | *Optional* - Set the submitter to a user other than the logged in user
`setPmNotes` | `pmNotes` | *Optional* - Notes for the project managers
`setProject` | `projectShortcode` | Set the project for which this submission will be created
`setSubmitter` | `submitter` | *Optional* - Set the submitter to a user other than the logged in user
`setUrgent` | `TRUE` or `FALSE` | *Optional* - Set priority. Defaults to Normal

## Document

```php
<?php
class PDDocument {
	public $data;
	public $name;
	public $sourceLanguage;
	public $targetLanguages;
	public $clientIdentifier;
	public $encoding = "UTF-8";
	public $fileformat;
	public $instructions;
	public $metadata;
	public function getDocumentInfo($submission)
	private function getTargetInfos()
	public function getResourceInfo()
}
?>
```

```ruby
class PDDocument
	attr_accessor :data
	attr_accessor :name
	attr_accessor :sourceLanguage
	attr_accessor :targetLanguages
	attr_accessor :clientIdentifier
	attr_accessor :encoding
	attr_accessor :fileformat
	attr_accessor :instructions
	attr_accessor :metadata
	def initialize 
		@encoding = "UTF-8"
		@clientIdentifier = nil
	end
	def getDocumentInfo(submission)
	end
	def getTargetInfos (submission)
	end
	def getResourceInfo
	end
end
```

```python
class PDDocument:
	data = ''
	name = ''
	sourceLanguage = ''
	targetLanguages = []
	clientIdentifier = None
	encoding = "UTF-8"
	fileformat = ''
	instructions = ''
	metadata = {}
```

This class will determine the necessary attributes to start a submission: 

Method | Returns | Sumary 
------ | ------- | -------
`getDocumentInfo` | Object | Internal method used by the UCF API
`getFileformat` | Array | File Format profile that defines the parsing rules for the document 
`getResourceInfo` | Object | Internal method used by the UCF API
`getSourceLanguage` | String | Shows the configured source language for an already sent document
`getTargetLanguages` | Array | Shows the list of configured target languages for an already sent document
`getMetadata` | Object | Shows the metadata configured for the document sent

Method | Parmeter | Sumary 
------ | ------- | -------
`setClientIdentifier` | `UID` at client's System | Specify a unique identifier for this document (if one exists) in the content management system
`setEncoding` | `encoding` | Set encoding for the document to be uploaded
`setFileformat` | `fileFormat` | If not set, defaults to configured `fileFormat` on project director
`setInstructions` | `instructions` | Additional metadata that you may want to attach to your document
`setSourceLanguage` | `sourceLanguage` | Set Source Language of the document that requires translation
`setTargetLanguages` | `targetLanguages` | Set target languages into which this document will be translated
`setMetadata` | `metadata` | Set metadata for the document being submitted for translation


## ReferenceDocument

Reference documents contain additional information which provide more context about the Documents that have been submitted for translation. eg. While submitting Indesign documents, the reference files usually contain the published source PDF The ReferenceDocuments do not require translation and are not accounted for in the translation wordcounts.

```php
<?php
class PDReferenceDocument {
	public $data;
	public $name;
	public function getResourceInfo()
}
?>
```

```ruby
class PDReferenceDocument
	attr_accessor :data
	attr_accessor :name
	
	def getResourceInfo
		resourceInfo = ResourceInfonew
		resourceInfo.size = @data.length
		resourceInfo.name = @name
		return resourceInfo
	end
end
```

```python
#No code snippet yet
```

Method | Returns | Sumary 
------ | ------- | -------
`getDataAsInputStream` | `InputStream` | Gets data as InputStream
`getName` | String | Gets the name of the document
`getResourceInfo` | Void |  

Method | Parmeter | Sumary 
------ | ------- | -------
`setData` | `data` | Set data from byte array or set data from `InputStream` or set data from string or set `data(byte[])` from string using encoding
`setName` | `name` | Set document name

## Workflow

```php
<?php
class PDWorkflow {
	public $name;
	public $ticket;
	function PDWorkflow($externalWorkflow)
}
?>
```

```ruby
class PDWorkflow
	attr_accessor :name;
	attr_accessor :ticket;
	def initialize(externalWorkflow)
		@name = externalWorkflow.name;
		@ticket = externalWorkflow.ticket;
	end
end
```

```python
#No code snippet yet
```

Method | Returns | Sumary 
------ | ------- | -------
`getWorkflowName` | String | returns the workflow name set up in PD
`getWorkflowTicket` | String | returns the workflow ticket for a given `WorkflowName`

## LanguageDirection

A language direction defines the source and target language direction for which users can submit translation requests.

```php
<?php
class PDLanguageDirection {
	public $sourceLanguage;
	public $sourceLanguageName;
	public $targetLanguage;
	public $targetLanguageName;
	function PDLanguageDirection($externalLanguageDirection)
}
?>
```

```ruby
class PDLanguageDirection
	attr_accessor :sourceLanguage
	attr_accessor :targetLanguage
end
```

```python
class PDLanguageDirection:
	sourceLanguage = ''
	targetLanguage = ''
	def __init__(self, externalLanguageDirection) :
		self.sourceLanguage = externalLanguageDirection.sourceLanguage.locale
		self.targetLanguage = externalLanguageDirection.targetLanguage.locale
```
Method | Returns | Sumary 
------ | ------- | -------
`getSourceLanguage` | String | gets the source language ISO code [e.g. en-US] configured in PD
`getSourceLanguageName` | String | gets the source language name [e.g. English (United States)] configured in PD
`getTargetLanguage` | String | gets the target language ISO code [e.g. de-DE] configured in PD
`getTargetLanguageName` | String | gets the source language name [e.g. German (Germany)] configured in PD


## Target

```php
<?php
class PDTarget {
	public $clientIdentifier;
	public $documentName;
	public $documentTicket;
	public $sourceLocale;
	public $targetLocale;
	public $metadata;
	public $ticket;
	public $wordCount;
	function PDTarget($externalTarget)
}
?>
```

```ruby
class PDTarget
	attr_accessor :clientIdentifier
	attr_accessor :documentName
	attr_accessor :documentTicket
	attr_accessor :sourceLocale
	attr_accessor :targetLocale
	attr_accessor :metadata
	attr_accessor :ticket
	attr_accessor :wordCount
	def initialize(externalTarget)
		@documentName = externalTarget.document.documentInfo.name
		@sourceLocale = externalTarget.sourceLanguage.locale
		@targetLocale = externalTarget.targetLanguage.locale
		@ticket = externalTarget.ticket
		@documentTicket = externalTarget.document.ticket
		@clientIdentifier = externalTarget.document.documentInfo.clientIdentifier
		@metadata = Hash.new
	end
end
```

```python
class PDTarget:
	clientIdentifier = None
	documentName = None
	documentTicket = None
	sourceLocale = None
	targetLocale = None
	metadata = None
	ticket = None
	wordCount = None
```

Method | Returns | Sumary 
------ | ------- | -------
`clientIdentifier` | String | `UID` configured by client when the document was sent
`documentName` | String | Document Name of the document that was submitted for translation
`documentTicket` | String | Document Ticket of the source document that was submitted for translation
`setadata` | Hash | Metadata in the form of key-value pairs set on the document that was submitted for translation
`sourceLocale` | String | Source locale (language ISO code) for this target
`submissionName` | String | Submission name
`targetLocale` | String | Locale (language ISO code) for this target
`ticket` | String | Target Ticket
`wordCount` | String | Amount of words for this target 

Method | Parmeter | Sumary 
------ | ------- | -------
`setDocumentName` | `documentName` | Set Document Name for the document that was submitted for translation


## WordCount

```php
<?php
class WordCount {
	public $golden; // int
	public $exact_100; // int
	public $fuzzy; // int
	public $repetitions; // int
	public $nomatch; // int
	public $total; // int
	function WordCount($_golden, $_exact_100, $_repetitions, $_nomatch, $_total)
?>
```

```ruby
class PDWordCount 
	attr_accessor :golden
	attr_accessor :exact_100
	attr_accessor :fuzzy
	attr_accessor :repetitions
	attr_accessor :nomatch
	attr_accessor :total
	def initialize(golden, exact_100, repetitions, nomatch, total) 
		@golden = golden;
		@exact_100 = exact_100;
		@repetitions = repetitions;
		@nomatch = nomatch;
		@total = total;
		@fuzzy = total - golden - exact_100 - repetitions - nomatch;
	end
end
```

```python
class PDWordCount:
	golden = None
	exact_100 = None
	fuzzy = None
	repetitions = None
	nomatch = None
	total = None
```

Please note that words are counted and analyzed per segment against a Translation Memory, TM. A TM is a database that stores segments, which can be sentences, paragraphs or sentence-like units (headings, titles or elements in a list) that have previously been translated, in order to aid human translators. The translation memory stores the source text and its corresponding translation in language pairs called “translation units”. Individual words are handled by terminology bases and are not within the domain of TM.

Method | Returns | Sumary 
------ | ------- | -------
golden | int | Total amount of words considered to be 100% matches in context against the TM (either because of previous and next segment match or due to attribute)
exact_100 | int | Total amoutn of words considered to be 100% matches against the TM
fuzzy | int | Total amoutn of words considered to be partially matching (99%-75%) against the TM
repetitions | int | Total amount of words that match in the same document
nomatch | int | Total amount of words that do not match (75%-0%) against the TM
total | int | Total amount of words counted on the document (`total` = `golden` + `exact_100` + `fuzzy` + `repetitions` + `nomatch`)

## CustomAttribute

```php
<?php
class PDCustomAttribute {
	public $mandatory;
	public $name;
	public $type;
	public $values;
	function PDCustomAttribute($customAttribute = NULL)
}
?>
```

```ruby
class PDCustomAttribute

	attr_accessor :mandatory
	attr_accessor :name
	attr_accessor :type
	attr_accessor :values
	
	def initialize(customAttribute = nil)
	end
end
```

```python
class PDCustomAttribute:
	mandatory = 'false'
	name = ''
	type = ''
	values = []
```

Each project can be configured to allow users to specify custom attributes for their submissions. The custom attributes can be either plain text, or an enum. Custom attributes can be used for reporting, billing etc. eg. You could specify a Cost Center as a custom attribute and instruct your account manager to invoice by cost-center

Method | Returns | Sumary 
------ | ------- | -------
`mandatory` | Boolean | Defines if the attribute is mandatory or not
`name` | string | Prints the attribute name
`type` | string | Prints the attribute type
`values` | Array | Prints the attribute value(s)

# Configuration Classes
## ProjectDirectorConfig

```php
<?php
class PDConfig {
	public $url;
	public $username;
	public $password;
	public $proxyConfig;
	public $userAgent;
}
?>
```

```ruby
class ProjectDirectorConfig
	attr_accessor :password
	attr_accessor :url
	attr_accessor :username
	attr_accessor :userAgent
end
```

```python
class ProjectDirectorConfig:
	url = None
	username = None
	password = None
	userAgent = None
```

Project director configuration

Method | Returns | Sumary 
------ | ------- | -------
`getPassword` | String | Get Project Director configured password 
`getProxy` | Object | Get the proxy configuration for communication between adaptor and GLC
`getTimeOut` | Int | Get the timeout value configured
`getUrl` | String | Get Project Director URL configured
`getUserAgent` | String | Returns the user agent configured
`getUsername` | String | Get Project Director configured username
`isEnableMTOM` | Boolean | Returns `TRUE` if MTOM is enabled

Method | Parmeter | Sumary 
------ | ------- | -------
`setEnableMTOM` | `TRUE` or `FALSE` | Set it to `false` to disable MTOM. Default is `true`
`setPassword` | `password` | Sets Project Director password
`setProxy` | `ProxyConfig` | Set proxy configuration for outbound traffic
`setTimeOut` | `timeOut` | Set response timeout for webservice calls
`setUrl` | `url` | Set the URL of the project director server to connect to
`setUserAgent` | `userAgent` | Sets the user Agent for this client. A user agent is any user friendly identifier which is used to categorize the logging on GlobalLink
`setUsername` | `username` | Sets Project Director username


## Proxy Config

```php
<?php
class ProxyConfig {
	public $proxyHost;
	public $proxyPort;
	public $proxyUser;
	public $proxyPassword;
}
?>
```

```ruby
#Not available for Ruby
```

```python
#Not available for Python
```

Method | Returns | Sumary 
------ | ------- | -------
`getProxyHost` | String | Returns the configured proxy server IP address or hostname
`getProxyPassword` | String | Returns the configured proxy user password
`getProxyPort` | Int | Returns the configured proxy server port
`getProxyUser` | String | Returns the configured proxy user

Method | Parmeter | Sumary 
------ | ------- | -------
`setProxyHost` | `proxyHost` | Set Proxy server IP address or hostname
`setProxyPassword` | `proxyPassword` | Proxy server user password
`setProxyPort` | `proxyPort` | Set Proxy server port
`setProxyUser` | `proxyUser` | Set Proxy user
