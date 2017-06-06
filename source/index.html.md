---
title: GlobalLink Connect API Reference

language_tabs:
  - csharp: .NET
  - java: Java
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



# Main Class - GLExchange

```csharp
public class GLExchange
{
	private const string PDVERSION = "4.18.0";
	private ProjectDirectorConfig pdConfig;
	private GL.Submission submission;
	private BasicHttpBinding binding;
	private UsernameToken USERNAMETOKEN;
	private EndpointAddress PROJECT_ENDPOINT_ADDRESS;
	private EndpointAddress TARGET_ENDPOINT_ADDRESS;
	private EndpointAddress SUBMISSION_ENDPOINT_ADDRESS;
	private EndpointAddress DOCUMENT_ENDPOINT_ADDRESS;
	private EndpointAddress USER_ENDPOINT_ADDRESS;
	private GL.Project[] projects;
	public GLExchange(ProjectDirectorConfig connectionConfig)
	private String _cleanup(String name)
	private SS.Date _convertDate(DateTime dateTime)
	private GL.Batch[] _convertBatchesToInternal(SS.Batch[] batches) {
	private GL.Target[] _convertTargetsToInternal(TS.Target[] targets)
	private GL.Project[] _convertProjectsToInternal(PS.Project[] projects)
	private GL.Submission[] _convertSubmissionsToInternal(SS.Submission[] list)
	private Dictionary<String, SubmissionInfo> _createSubmissionInfos()
	private SS.SubmissionInfo _createSubmissionInfo(int count)
	private bool _endpointExists()
	private String[] _getSubmitters(String projectShortCode)
	private Boolean _isSubmitterValid(String projectShortCode, String submitter)
	private Boolean _validateSubmission()
	public String cancelDocument(String targetTicket)
	public String cancelDocument(String documentTicket, String locale)
	public String cancelSubmission(String submissionTicket)
	public Dictionary<string, HashSet<string>> getAvailableLanguageDirections(){
	public GL.Target[] getCancelledTargetsByDocuments(String[] documentTickets, int maxResults)
	public GL.Target[] getCancelledTargetsBySubmissions(String[] submissionTickets, int maxResults)
	public GL.Target[] getCancelledTargetsByProjects(String[] projectTickets, int maxResults)
	public GL.Target[] getCompletedTargets(GL.Project project, int maxResults)
	public GL.Target[] getCompletedTargetsByProjects(String[] projectTickets, int maxResults)
	public GL.Target[] getCompletedTargetsBySubmissions(String[] submissionTickets, int maxResults)
	public GL.Target[] getCompletedTargetsByDocuments(String[] documentTickets, int maxResults)
	public Target[] getCompletedTargetsByDocument(String documentTicket, int maxResults)
	public LanguagePhaseInfo getLanguagePhaseInfo(String submissionTicket, String batchName, String targetLanguage, String phaseName)
	public GL.Project getProject(String projectShortcode)
	public GL.Project[] getProjects()
	private GL.Project[] getUserProjects()
	private SS.Submission findSubmission(string submissionTicket)
	public GL.Batch[] getSubmissionBatches(String submissionTicket)
	public string getSubmissionName(String submissionTicket)
	public long getSubmissionId(String submissionTicket)
	public GL.ItemStatusEnum getSubmissionStatusEnum( String submissionTicket ) {
	public string getSubmissionStatus(String submissionTicket)
	public String[] getSubmissionTickets()
	public GL.Submission[] getUnstartedSubmissions(GL.Project project)
	public void initSubmission(GL.Submission submission)
	public bool isSubmissionComplete(String submissionTicket)
	public String sendDownloadConfirmation(String targetTicket)
	public void setConnectionConfig(ProjectDirectorConfig connectionConfig)
	public String[] startSubmission()
	public String uploadReference(GL.ReferenceDocument referenceDocument)
	public String uploadTranslatable(GL.Document document)
}
```

```java
public class GLExchange
extends Object

//Constructor Detail
public GLExchange(ProjectDirectorConfig connectionConfig)
	throws Exception

//Method Detail
	public String cancelDocument(String documentTicket)
	public String cancelDocument(String documentTicket, String locale)
	public String cancelSubmission(String submissionTicket)
	public String cancelSubmission(String submissionTicket, String comment)
	public InputStream downloadCompletedTarget(String ticket)
	public InputStream[] downloadPreliminaryTargets(org.gs4tr.projectdirector.model.dto.SubmissionWorkflowInfo submissionWorkflowInfo, boolean doClaim)
				throws InterruptedException
	public InputStream[] downloadTranslationKit(org.gs4tr.projectdirector.model.dto.SubmissionWorkflowInfo submissionWorkflowInfo)
				throws Exception
	public org.gs4tr.projectdirector.model.dto.SubmissionWorkflowInfo[] findAvailableWorkflowInfosForClaim(int limit)
	public org.gs4tr.projectdirector.model.dto.SubmissionWorkflowInfo[] findAvailableWorkflowInfosForDownload(int limit)
	public String[] getAvailableSubmissions(String STATE)
				throws Exception
	public Target[] getCancelledTargets(int maxResults)
	public Target[] getCancelledTargets(String submissionTicket, int maxResults)
	public Target[] getCompletedTargets(int maxResults)
	public Target[] getCompletedTargets(Project project, int maxResults)
	public Target[] getCompletedTargetsByDocuments(List<String> documentTickets, int maxResults)
	public Project getProject(String shortCode)
	public Project[] getProjects()
	public String getSubmissionName(String submissionTicket)
				throws Exception
	public String[] getSubmissionTickets()
				throws Exception
	public Submission[] getUnstartedSubmissions(Project project)
	public void initSubmission(Submission submission)
`				throws Exception
	public boolean isSubmissionComplete(String submissionTicket)
				throws Exception
	public String getSubmissionStatus(String submissionTicket)
				throws Exception
	public String[] startSubmission()
				throws Exception
	public String uploadReference(ReferenceDocument referenceDocument)
				throws Exception
	public String uploadTranslatable(Document document)
				throws Exception
	public String uploadTranslationKit(String fileName, byte[] inputStream)
				throws InterruptedException, IOException
```

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
`cancelDocument` |  | Cancel document for all languages or Cancel document for specified target language
`cancelSubmission` |  | Cancel Submission for all languages or Cancel Submission for all languages with comment
`downloadCompletedTarget` |  | Downloads target document from PD or Download all complted targets
`getCancelledTargets` | Array of cancelled targets | Get cancelled targets for all projects or Get cancelled targets for a submission
`getCompletedTargets` | Array of completed targets | Get completed targets for all projects or Get completed targets for specified project or Get completed targets for submission
`getCompletedTargetsByDocuments` | Array of completed targets | Get completed targets by document tickets
`getProject` | Project with specified shortcode | Get project by it`s shortcode
`getProjects` | Array of Projects with subprojects to which the logged in user has access to | Get all user projects
`getSubmissionName` | Submission name for the specified ticket. | Get Submission name for specified ticket
`getSubmissionTickets` | Submission ticket. | Get Submission ticket if a submission has been initialized
`getUnstartedSubmissions` | Array of Submissions that have not been started. | Get Unstarted Submissions
`initSubmission` |  | Initialize a new Submission
`isSubmissionComplete` | True if submission is complete. | Get Submission status for specified ticket
`getSubmissionStatus` | True if submission is complete. | Get Submission status for specified ticket
`sendDownloadConfirmation` |  | Sends confirmation that the target resources was downloaded successfully by the customer
`startSubmission` | Submission Ticket | Start Submission
`uploadReference` |  | Upload reference file for submission
`uploadTranslatable` | Document Ticket | Uploads the document to project director for translation
`uploadTranslationKit` |  |  

# Models

## Project

```csharp
public class Project
{
	public String shortcode { get; set; }
	public String name { get; set; }
	public String ticket { get; set; }
	public LanguageDirection[] languageDirections { get; set; }
	public String[] fileFormats { get; set; }
	public Workflow[] workflows { get; set; }
	public CustomAttribute[] customAttributes { get; set; }
	public String[] submitters { get; set; }
	public Project(PS.Project project)
	}
```

```java
public class Project
extends Object

//Constructor Detail
public Project(org.gs4tr.projectdirector.model.dto.Project project)

//Method Detail
	public CustomAttribute[] getCustomAttributes()
	public String[] getFileFormats()
	public LanguageDirection[] getLanguageDirections()
	public String getName()
	public String getShortcode()
	public String[] getSubmitters()
	public String getTicket()
	public Workflow[] getWorkflows()
	public void setSubmitters(String[] submitters)
```

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
`getCustomAttributes` | List of configured Custom Attributes for this project | Get Custom Attributes
`getFileFormats` | List of configured file formats for this project | Get File Formats
`getLanguageDirections` | List of configured language directions for this project | Get language directions
`getName` | Descriptive project name | Get Project Name
`getShortcode` | User friendly Project Short Code | Get Project Short Code
`getSubmitters` |  |  
`getTicket` | Project Ticket that is used for internal API communication | Get Project Ticket
`getWorkflows` | List of configured workflows for this project | Get Workflows
`setSubmitters` |  |  

## Submission

```csharp
public class Submission
{
	public Dictionary<String, String> customAttributes { get; set; }
	public DateTime dueDate { get; set; }
	public String instructions { get; set; }
	public Boolean isUrgent { get; set; }
	public Dictionary<String, String> metadata { get; set; }
	public String name { get; set; }
	public String pmNotes { get; set; }
	public Project project { get; set; }
	public List<String> tickets { get; set; }
	public String submitter { get; set; }
	public Workflow workflow { get; set; }
	public String owner { get; set; }
	public String paClientTicket { get; set; }
	public Submission()
	public Submission(SubmissionServiceRef.Submission submission)
	public void setTickets(String[] tickets) {
	public void addTicket(String ticket)
}
```

```java
public class Submission
extends Object

//Constructor Detail
public Submission()

//Method Detail
	public HashMap<String,String> getCustomAttributes()
	public Date getDueDate()
	public String getInstructions()
	public HashMap<String,String> getMetadata()
	public String getName()
	public String getOwner()
	public String getPmNotes()
	public Project getProject()
	public String getSubmitter()
	public String[] getTickets()
	public Workflow getWorkflow()
	public boolean isUrgent()
	public void setCustomAttributes(HashMap<String,String> customAttributes)
	public void setDueDate(Date dueDate)
	public void setInstructions(String instructions)
	public void setMetadata(HashMap<String,String> metadata)
	public void setName(String submissionName)
	public void setOwner(String owner)
	public void setPmNotes(String pmNotes)
	public void setProject(Project project)
	public void setSubmitter(String submitter)
	public void setTickets(String[] tickets)
	public void addTicket(String ticket)
	public void setUrgent(boolean isUrgent)
	public void setWorkflow(Workflow workflow)
```

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
`getCustomAttributes` |  |  
`getDueDate` | Date | Returns due date of submission
`getInstructions` | String | Returns submission instructions
`getMetadata` | Hash | Returns submission metadata
`getName` | String | Returns submission name
`getPmNotes` | String | Returns submission pm notes
`getProject` | String | Returns submission project
`getSubmitter` | String | Returns submission submitter
`isUrgent` | Boolean | Returns if submission is urgent or not
`setCustomAttributes` |  | *Optional* - Set custom attributes. `Project.getCustomAttributes()` gets you the list of configured attributes for the project
`setDueDate` |  | *Optional* - Due date by when the submission should be completed in Project Director. This should always be greater than current date. If due date is not specified, Project Director will rely on the configured language model to calculate a due date
`setInstructions` |  | *Optional* - Set instructions for the translators
`setMetadata` |  | *Optional* - Key-value pair of metadata
`setName` |  | Name of the submission that will show up in Project Director
`setOwner` |  | *Optional* - Set the submitter to a user other than the logged in user
`setPmNotes` |  | *Optional* - Notes for the project managers
`setProject` |  | Set the project for which this submission will be created
`setSubmitter` |  | *Optional* - Set the submitter to a user other than the logged in user
`setUrgent` |  | *Optional* - Set priority. Defaults to Normal

## Document

```csharp
public class Document : ReferenceDocument
{
	public String sourceLanguage { get; set; }
	public String[] targetLanguages { get; set; }
	public String clientIdentifier { get; set; }
	public String encoding { get; set; }
	public String fileformat { get; set; }
	public String instructions { get; set; }
	public Dictionary<String, String> metadata { get; set; }
	public Dictionary<String, String> targetWorkflowNames { get; set; }
	public Document()
	public DocumentInfo getDocumentInfo(Submission submission)
	private TargetInfo[] getTargetInfos(Submission submission)
	public new ResourceInfo getResourceInfo()
}
```

```java
public class Document
extends ReferenceDocument

//Constructor Detail
public Document()

//Method Detail
	public org.gs4tr.projectdirector.model.dto.DocumentInfo getDocumentInfo(Submission submission)
	public String getFileformat()
	public org.gs4tr.projectdirector.model.dto.ResourceInfo getResourceInfo()
	public String getSourceLanguage()
	public String[] getTargetLanguages()
	public HashMap<String,String> getTargetWorkflowNames()
	public void setClientIdentifier(String clientIdentifier)
	public void setEncoding(String encoding)
	public void setInstructions(String instructions)
	public void setMetadata(HashMap<String,String> metadata)
	public void setSourceLanguage(String sourceLanguage)
	public void setTargetLanguages(String[] targetLanguages)'
	public void setTargetWorkflowNames(HashMap<String,String> targetWorkflowNames)
```

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
`getDocumentInfo` | `DocumentInfo` object | Internal method used by the UCF API
`getFileformat` |  |  
`getResourceInfo` | `ResourceInfo` object | Internal method used by the UCF API
`getSourceLanguage` |  |  
`getTargetLanguages` |  |  
`getTargetWorkflowNames` |  |  
`setClientIdentifier` |  | Specify a unique identifier for this document (if one exists) in the content management system
`setEncoding` |  | Set encoding
`setFileformat` |  | Defaults to configured `fileFormat` on project director
`setInstructions` |  | Additional metadata that you may want to attach to your document
`setSourceLanguage` |  | Set Source Language of the document
`setTargetLanguages` |  | Set target languages into which this document will be translated
`setTargetWorkflowNames` |  |  

## ReferenceDocument

Reference documents contain additional information which provide more context about the Documents that have been submitted for translation. eg. While submitting Indesign documents, the reference files usually contain the published source PDF The ReferenceDocuments do not require translation and are not accounted for in the translation wordcounts.

```csharp
public class ReferenceDocument
{
	public byte[] data { get; set; }
	public String name { get; set; }
	public void setDataFromString(String data)
	public void setDataFromMemoryStream(MemoryStream data)
	public ResourceInfo getResourceInfo()
	public String getDataAsString()
}
```

```java
public class ReferenceDocument
extends Object

//Constructor Detail
public ReferenceDocument()

//Method Detail
	public byte[] getData()
	public InputStream getDataAsInputStream()
	public String getName()
	public org.gs4tr.projectdirector.model.dto.ResourceInfo getResourceInfo()
	public void setData(byte[] data)
	public void setData(byte[] data)
	public void setData(InputStream inputStream)
			throws IOException
	public void setData(String data,
			    String encoding)
			throws UnsupportedEncodingException
	public void setName(String name)
```

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
`getResourceInfo` |  |  
`setData` |  | Set data from byte array or set data from `InputStream` or set data from string or set `data(byte[])` from string using encoding
`setName` |  | Set document name

## Workflow

```csharp
public class Workflow
{
	public String name { get; set; }
	public String ticket { get; set; }
	public Workflow(WorkflowDefinition definition)
	public Workflow(GlobalLink.Connect.SubmissionServiceRef.WorkflowDefinition definition)
}
```

```java
public class Workflow
extends Object

//Constructor Detail
public Workflow(org.gs4tr.projectdirector.model.dto.WorkflowDefinition definition)

//Field Detail
	public String name
	public String ticket
```

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

## LanguageDirection

A language direction defines the source and target language direction for which users can submit translation requests.

```csharp
public class LanguageDirection
{
	public String sourceLanguage { get; set; }
	public String targetLanguage { get; set; }
	public LanguageDirection(ProjectLanguageDirection direction)
}
```

```java
public class LanguageDirection
extends Object

//Constructor Detail
public LanguageDirection(org.gs4tr.projectdirector.model.dto.ProjectLanguageDirection direction)

//Field Detail
	public String sourceLanguage
	public String targetLanguage
	public TMProfile TM
```

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

## Target

```csharp
public class Target
{
	public String clientIdentifier { get; set; }
	public String documentName { get; set; }
	public String documentTicket { get; set; }
	public String sourceLocale { get; set; }
	public String targetLocale { get; set; }
	public Dictionary<String, String> metadata { get; set; }
	public String submissionName { get; set; }
	public String ticket { get; set; }
	public WordCount wordCount { get; set; }
	public Target(TS.Target dtoTarget)
	public MemoryStream  getData(GLExchange xchange)
	public String sendDownloadConfirmation(GLExchange xchange)
}
```

```java
public class Target
extends Object

//Constructor Detail
public Target(org.gs4tr.projectdirector.model.dto.Target dtoTarget)

//Method Detail
	public String getClientIdentifier()
	public String getDocumentName()
	public String getDocumentTicket()
	public HashMap<String,String> getMetadata()
	public String getSourceLocale()
	public String getSubmissionName()
	public String getTargetLocale()
	public String getTicket()
	public WordCount getWordCount()
	public InputStream getData()
	public InputStream getData(GLExchange xchange)
	public void setData(InputStream data)
	public void setDocumentName(String documentName)
```

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
`getClientIdentifier` | String |  
`getDocumentName` | String Name of the document that was submitted for translation | Get Document Name
`getDocumentTicket` | String Document Ticket of the source document that was submitted for translation | Get Document Ticket
`getMetadata` | Hash Metadata | Get metadata in the form of key-value pairs set on the document that was submitted for translation
`getSourceLocale` | String Source locale of this target | Get Source locale (language ISO code)
`getSubmissionName` | String | Get the Submission name
`getTargetLocale` | String Target locale of this target | Get the Locale (language ISO code) for this target
`getTicket` | String Target ticket | Get Target Ticket
`getWordCount` |  |  
`getData` | `InputStream` containing the translated content | Get translated data or get translated data and download if empty
`setDocumentName` |  | Set Document Name

## TM Profile

```csharp
///No code snippet yet
```

```java
public class TMProfile
extends Object

//Constructor Detail
public TMProfile(String url,
		 String username,
		 String password,
		 String tMName)

//Method Detail
	public String getPassword()
	public String getTMName()
	public String getUrl()
	public String getUsername()
```

```php
<?php
//No code snippet yet
?>
```

```ruby
#No code snippet yet
```

```python
#No code snippet yet
```

## WordCount

```csharp
public class WordCount
{
	public int golden { get; set; }
	public int exact_100 { get; set; }
	public int fuzzy { get; set; }
	public int repetitions { get; set; }
	public int nomatch { get; set; }
	public int total { get; set; }
	public WordCount(int _golden, int _exact_100, int _repetitions, int _nomatch, int _total)
	{
		this.golden = _golden;
		this.exact_100 = _exact_100;
		this.fuzzy = _total - _golden - _exact_100 - _repetitions - _nomatch;
		this.repetitions = _repetitions;
		this.nomatch = _nomatch;
		this.total = _total;
	}
}
```

```java
public class WordCount
extends Object

//Constructor Detail
public WordCount(int _golden,
		 int _exact_100,
		 int _repetitions,
		 int _nomatch,
		 int _total)

//Method Detail
	public int getExact_100()
	public int getFuzzy()
	public int getGolden()
	public int getNomatch()
	public int getRepetitions()
	public int getTotal()
	public void setExact_100(int exact_100)
	public void setFuzzy(int fuzzy)
	public void setGolden(int golden)
	public void setNomatch(int nomatch)
	public void setRepetitions(int repetitions)
	public void setTotal(int total)
```

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



## CustomAttribute

```csharp
public class CustomAttribute
{
	public bool mandatory { get; set; }
	public String name { get; set; }
	public String type { get; set; }
	public String values { get; set; }
}
```

```java
public class CustomAttribute
extends Object

//Constructor Detail
public CustomAttribute(boolean mandatory,
	String name,
	String type,
	String values)
```

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



# Configuration
## ProjectDirectorConfig

```csharp
private static ProjectDirectorConfig getPDConfig()
{
	ProjectDirectorConfig config = new ProjectDirectorConfig();
	string url = ConfigurationManager.AppSettings[CONFIG_URL];
	string username = ConfigurationManager.AppSettings[CONFIG_USERNAME];
	string password = ConfigurationManager.AppSettings[CONFIG_PASSWORD];
	string userAgent = ConfigurationManager.AppSettings[CONFIG_USERAGENT];
	config.userAgent = userAgent;
	return config;
}
```

```java
public class ProjectDirectorConfig
extends Object

//Constructor Detail
public ProjectDirectorConfig()

//Method Detail
	public String getPassword()
	public ProxyConfig getProxy()
	public int getTimeOut()
	public String getUrl()
	public String getUserAgent()
	public String getUsername()
	public Boolean isEnableMTOM()
	public void setEnableMTOM(Boolean enableMTOM)
	public void setPassword(String password)
	public void setProxy(ProxyConfig proxy)
	public void setTimeOut(int timeOut)
	public void setUrl(String url)
	public void setUserAgent(String userAgent)
	public void setUsername(String username)
```

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
`getPassword` | String Project Director password | Get Project Director configured password 
`getProxy` | Proxy configuration for outbound traffic | Get the proxy configuration for communication between adaptor and GLC
`getTimeOut` | Int Response timeout for webservice calls | Get the timeout value 
`getUrl` | String URL or IP address of the Project Director server | Get Project Director URL
`getUserAgent` | String user Agent for this client | Returns 
`getUsername` | Project Director username | Get Project Director configured username 
`isEnableMTOM` | Boolean | Returns `true` if MTOM is enabled
`setEnableMTOM` |  | Set it to `false` to disable MTOM. Default is `true`
`setPassword` |  | Sets Project Director password
`setProxy` |  | Set proxy configuration for outbound traffic
`setTimeOut` |  | Set response timeout for webservice calls
`setUrl` |  | URL of the project director server to connect to
`setUserAgent` |  | Sets the user Agent for this client. A user agent is any user friendly identifier which is used to categorize the logging on GlobalLink
`setUsername` |  | Sets Project Director username

## Proxy Config

```csharp
///No code snippet yet
```

```java
public class ProxyConfig
extends Object

//Constructor Detail
public ProxyConfig()

//Method Detail
	public String getProxyHost()
	public String getProxyPassword()
	public int getProxyPort()
	public String getProxyUser()
	public void setProxyHost(String proxyHost)
	public void setProxyPassword(String proxyPassword)
	public void setProxyPort(int proxyPort)
	public void setProxyUser(String proxyUser)
```

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
#No code snippet yet
```

```python
#No code snippet yet
```

Method | Returns | Sumary 
------ | ------- | -------
`getProxyHost` | String | Returns proxy server IP address or hostname
`getProxyPassword` | String | Returns proxy user password
`getProxyPort` | Int | Returns proxy server port
`getProxyUser` | String | Returns proxy user
`setProxyHost` |  | Set Proxy server IP address or hostname
`setProxyPassword` |  | Proxy server user password
`setProxyPort` |  | Set Proxy server port
`setProxyUser` |  | Set Proxy user
