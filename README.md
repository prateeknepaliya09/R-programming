<h1>Running the script</h1>
<ul>
<li>Clone this repository</li>
<li>Download the <a href="https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip">data set</a> and extract. It should result in a <code>UCI HAR Dataset</code> folder that has all the files in the required structure.</li>
<li>Change current directory to the UCI HAR Dataset folder.</li>
<li>Run <code>Rscript <path to>run_analysis.R</code></li>
<li>The tidy dataset should get created in the current directory as tidy.txt</li>
</ul>
<h1>Assumptions</h1>
<ul>
<li>The training and test data are available in folders named <code>train</code> and <code>test</code> respectively.</li>
<li>For each of these data sets:
<ul>
<li>Measurements are present in <code>X_&lt;dataset&gt;.txt</code> file</li>
<li>Subject information is present in <code>subject_&lt;dataset&gt;.txt</code> file</li>
<li>Activity codes are present in <code>y_&lt;dataset&gt;.txt</code> file</li>
</ul>
</li>
<li>All activity codes and their labels are in a file named <code>activity_labels.txt</code>.</li>
<li>Names of all measurements taken are present in file <code>features.txt</code> ordered and indexed as they appear in the <code>X_&lt;dataset&gt;.txt</code> files.</li>
<li>All columns representing means contain <code>...mean()</code> in them.</li>
<li>All columns representing standard deviations contain <code>...std()</code> in them.</li>
</ul>

<h1>Data Preparation Steps</h1>

<ol>
<li>For each of the training and test datasets, 

<ol>
<li>Read the <code>X</code> values</li>
<li>Take a subset of the columns representing only the mean and standard deviation values. Subsetting is done early on to conserve memory.</li>
<li>Associate additional columns to represent activity IDs and subject IDs read from <code>y_&lt;dataset&gt;.txt</code> and <code>subject_&lt;dataset&gt;.txt</code> files respectively.</li>
<li>Assign column names by manipulating the measurement names in <code>features.txt</code> to remove spaces and convert them to camel case.</li>
</ol>
</li>
<li>Merge the training and the test sets, read as in step 1 to create one data set.</li>
<li>Associate an additional column with descriptive activity names as specified in <code>activity_labels.txt</code>.</li>
<li>Melt the dataset by specifying activity ID, name and subject ID as the only ID variables.</li>
<li>Re cast the melted dataset with activity name and subject id as the only IDs and <code>mean</code> as the aggregator function.</li>
<li>Save the resultin re-casted dataset as <code>tidy.txt</code>
</li>
</ol>
