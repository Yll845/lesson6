# lesson6
<?php
    // 'w' - Opens a file for write-only mode. If a file does not exist then a new file is created and if the file already exists then the line of the contents of the file are erased for write-only mode.
    // 'r' - File is opened for read-only mode.
    // 'a' - File is opened for write-only mode. The file pointer points to the end of the file. Existing data in the file is preserved.
    // 'w+' - Opens the file for read and write mode. If a file does not exist then a new file is created and if the file already exists the contents of the file are erased.
    // 'a+' - This is opened for write/read mode.
    // 'x' - Newly file is created for write-only mode.

    $file = fopen("example.txt", "w"); // Open or create 'example.txt' for writing
    if ($file) {
        $content = "Hello, this is a line of text written to the file.\n";
        fwrite($file, $content);
    
        $moreContent = "Here's another line of text.\n";
        fwrite($file, $moreContent);
    
        fclose($file);
        echo "Data written to file successfully.\n";
    } else {
        echo "Failed to open the file for writing.\n";
    }
    
    
    $file = fopen("example.txt", "r");
    if ($file) {
        
        while (!feof($file)) {
            $line = fread($file, 8192); 
            echo $line;
        }
    
        
        fclose($file);
    } else {
        echo "Failed to open the file for reading.\n";
    }
    
    
    $newContent = "This content is written using file_put_contents.\n";
    file_put_contents("example.txt", $newContent, FILE_APPEND); // Append new content
    
    echo "Additional content written using file_put_contents.\n";

echo "Script is running";

     
function writeToFile($message) {
  
     $file = fopen("example.text", "a");
    
     
     if ($file) {
         
         fwrite($file, $message . PHP_EOL);

        
         fclose($file);
    } else {
       
     echo "Could not open the file!";   
    }
 }






function readFromFile(){
    $file = fopen("example.txt", 'r');

    
    if($file){
        echo "Content of example.txt";

        
        while(!feof($file)){
            $line = fgets($file);
            echo htmlspecialchars(($line)."<br>");
        }
        fclose($file);
    } else{
        echo "Failed to open the file for reading!!";
    }
    
}


function quickWriteToTheFile($message){
    file_put_contents("example.txt", $message."PHP_EQL");
    echo "Message written to the file using file_put_contect!<br>";
}


writeToFile("This is a sample log message!!");
quickWriteToTheFile("This will overwrite everything with a new message!!");
readFromFile();

        

    ?>
