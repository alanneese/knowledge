include('../inc/dbconn.php');
include('../inc/bug.php'); 

$debugging='yes';

if ($debugging=='yes') {
  // Get the next_screen_id. 
  $sql = "select * from `xref` where `thekey` = '" . "next_screen_id" . "'";
  $result = $conn->query($sql);
  $row = $result->fetch_assoc();
  $next_screen_id=$row["line1"];
  // Add one and rewrite it. 
  //////////////////////////////////////////////////////////////////////////////
  // $screenId must be preset in order for all bug statements to work properly. 
  //////////////////////////////////////////////////////////////////////////////
  $screenId = ++$next_screen_id;
  $sql = "update xref set `line1` = '".$screenId."' where `thekey` = 'next_screen_id'";
  $result = $conn->query($sql);
  bug('clear','');
  bug('===== projectMarks/index.php =====','');       
}