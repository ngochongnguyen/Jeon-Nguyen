# Jeon-Nguyen
import java.util.*;
class TreeNode{
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(){}
    TreeNode(int val){
        this.val = val;
    }
    TreeNode(int val, TreeNode left, TreeNode right){
        this.val = val;
        this.left = left;
        this.right = right;
    }


}
public class AvgLevelsOfBST {
    public static List<Double> averageOfLevels(TreeNode root){
        List<Double> res = new ArrayList<>();
        if(root == null){
            return res; // neu cay rong thi tra ve res rong
        }
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root); // them nut goc
        while(!queue.isEmpty()){
            int levelSize = queue.size();
            double sum = 0;
            for(int i=0;i<levelSize;i++){
                TreeNode currNode = queue.poll();
                sum += currNode.val;

                if(currNode.left != null){
                    queue.add(currNode.left);
                }

                if(currNode.right != null){
                    queue.add(currNode.right);
                }
            }
            res.add(sum / levelSize);
        }
        return res;

    }

    public static void main(String[] args) {
        // TEST CASE 1 :
        TreeNode root1 = new TreeNode(3);
        root1.left = new TreeNode(9);
        root1.right = new TreeNode(20);
        root1.right.left = new TreeNode(15);
        root1.right.right = new TreeNode(7);

        List<Double> res = averageOfLevels(root1);
        System.out.println("Res la : " + res);

        // TEST CASE 2 :

        TreeNode root2 = new TreeNode(3);
        root2.left = new TreeNode(9);
        root2.left.left = new TreeNode(15);
        root2.left.right = new TreeNode(7);
        root2.right = new TreeNode(20);
        List<Double> res2 = averageOfLevels(root2);
        System.out.println("Res la : " + res2);
    

    }

}
